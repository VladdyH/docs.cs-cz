---
title: "Ukázka zprostředkovatele s objekty COM: klient .NET a server COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, samples
- COM interop, samples
ms.assetid: a3f752bb-8945-4e1b-8163-71def6e9f137
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3a2db2aba0904aac89bf5fe73c715ff7a5eeb5f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="com-interop-sample-net-client-and-com-server"></a>Ukázka zprostředkovatele s objekty COM: klient .NET a server COM
Tento příklad znázorňuje jak [klient .NET](#cpconcominteropsamplenetclientcomserveranchor1), vytvořené pro přístup k [COM server](#cpconcominteropsamplenetclientcomserveranchor2), vytvoří instanci COM coclass a volá členy třídy, provádění výpočtů hypotéky.  
  
 V tomto příkladu klient vytvoří a volá instance **úvěr** coclass, předá čtyři argumenty (jedna z těchto čtyř se rovná nule) na instance a zobrazí výpočtů. Fragmenty kódu z této ukázce se zobrazí v této části.  
  
<a name="cpconcominteropsamplenetclientcomserveranchor1"></a>   
## <a name="net-client"></a>Klient .NET  
  
```vb  
Imports System  
Imports Microsoft.VisualBasic  
Imports LoanLib  
  
Public Class LoanApp  
  
    Public Shared Sub Main()  
        Dim Args As String()  
        Args = System.Environment.GetCommandLineArgs()  
  
        Dim ln As New Loan()  
  
        If Args.Length < 5 Then  
            Console.WriteLine("Usage: ConLoan Balance Rate Term Payment")  
            Console.WriteLine(" Either Balance, Rate, Term, or Payment " _  
                                & "must be 0")  
            Exit Sub  
        End If  
  
        ln.OpeningBalance = Convert.ToDouble(Args(1))  
        ln.Rate = Convert.ToDouble(Args(2)) / 100.0  
        ln.Term = Convert.ToInt16(Args(3))  
        ln.Payment = Convert.ToDouble(Args(4))  
  
        If ln.OpeningBalance = 0.0 Then  
            ln.ComputeOpeningBalance()  
        End If  
        If ln.Rate = 0.0 Then  
            ln.ComputeRate()  
        End If  
        If ln.Term = 0 Then  
            ln.ComputeTerm()  
        End If  
        If ln.Payment = 0.0 Then  
            ln.ComputePayment()  
        End If   
        Console.WriteLine("Balance = {0,10:0.00}", ln.OpeningBalance)  
        Console.WriteLine("Rate    = {0,10:0.0%}", ln.Rate)  
        Console.WriteLine("Term    = {0,10:0.00}", ln.Term)  
        Console.WriteLine("Payment = {0,10:0.00}" & ControlChars.Cr, _  
                          ln.Payment)  
  
        Dim MorePmts As Boolean  
        Dim Balance As Double = 0.0  
        Dim Principal As Double = 0.0  
        Dim Interest As Double = 0.0  
  
        Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", _  
           "Nbr", "Payment", "Principal", "Interest", "Balance")  
        Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", _  
           "---", "-------", "---------", "--------", "-------")  
  
        MorePmts = ln.GetFirstPmtDistribution(ln.Payment, Balance, _  
           Principal, Interest)  
  
        Dim PmtNbr As Short  
  
        While MorePmts  
  
            Console.WriteLine("{0,4}{1,10:0.00}{2,12:0.00}{3,10:0.00}" _  
              & "{4,12:0.00}", PmtNbr, ln.Payment, Principal, Interest,  
              Balance)  
            MorePmts = ln.GetNextPmtDistribution(ln.Payment, Balance, _  
              Principal, Interest)  
            PmtNbr += CShort(1)  
        End While  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using LoanLib;  
  
public class LoanApp {  
   public static void Main(String[] Args) {  
  
      Loan ln = new Loan();  
  
      if (Args.Length < 4)   
      {  
         Console.WriteLine("Usage: ConLoan Balance Rate Term Payment");  
         Console.WriteLine("    Either Balance, Rate, Term, or Payment   
            must be 0");  
         return;  
      }  
  
      ln.OpeningBalance = Convert.ToDouble(Args[0]);  
      ln.Rate = Convert.ToDouble(Args[1])/100.0;  
      ln.Term = Convert.ToInt16(Args[2]);  
      ln.Payment = Convert.ToDouble(Args[3]);  
  
      if (ln.OpeningBalance == 0.00) ln.ComputeOpeningBalance();  
      if (ln.Rate == 0.00) ln.ComputeRate();  
      if (ln.Term == 0) ln.ComputeTerm();  
      if (ln.Payment == 0.00) ln.ComputePayment();  
  
      Console.WriteLine("Balance = {0,10:0.00}", ln.OpeningBalance);  
      Console.WriteLine("Rate    = {0,10:0.0%}", ln.Rate);  
      Console.WriteLine("Term    = {0,10:0.00}", ln.Term);  
      Console.WriteLine("Payment = {0,10:0.00}\n", ln.Payment);  
  
      bool MorePmts;  
      double Balance = 0.0;  
      double Principal = 0.0;  
      double Interest = 0.0;  
  
      Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", "Nbr", "Payment",  
        "Principal", "Interest", "Balance");  
      Console.WriteLine("{0,4}{1,10}{2,12}{3,10}{4,12}", "---", "-------",  
        "---------", "--------", "-------");  
  
      MorePmts = ln.GetFirstPmtDistribution(ln.Payment, out Balance,   
        out Principal, out Interest);  
  
      for (short PmtNbr = 1; MorePmts; PmtNbr++) {  
         Console.WriteLine("{0,4}{1,10:0.00}{2,12:0.00}{3,10:0.00}  
           {4,12:0.00}", PmtNbr, ln.Payment, Principal, Interest,  
            Balance);  
         MorePmts = ln.GetNextPmtDistribution(ln.Payment, ref Balance,   
           out Principal, out Interest);   
      }  
    }  
}  
```  
  
<a name="cpconcominteropsamplenetclientcomserveranchor2"></a>   
## <a name="com-server"></a>COM Server  
  
```cpp  
// Loan.cpp : Implementation of CLoan  
#include "stdafx.h"  
#include "math.h"  
#include "LoanLib.h"  
#include "Loan.h"  
  
static double Round(double value, short digits);   
  
STDMETHODIMP CLoan::get_OpeningBalance(double *pVal)  
{  
    *pVal = OpeningBalance;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_OpeningBalance(double newVal)  
{  
    OpeningBalance = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Rate(double *pVal)  
{  
    *pVal = Rate;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Rate(double newVal)  
{  
    Rate = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Payment(double *pVal)  
{  
    *pVal = Payment;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Payment(double newVal)  
{  
    Payment = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_Term(short *pVal)  
{  
    *pVal = Term;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_Term(short newVal)  
{  
    Term = newVal;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputePayment(double *pVal)  
{  
    Payment = Round(OpeningBalance * (Rate /   
        (1 - pow((1 + Rate), -Term))),2);  
    *pVal = Payment;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeOpeningBalance(double *pVal)  
{  
    OpeningBalance = Round(Payment / (Rate /   
        (1 - pow((1 + Rate), -Term))),2);  
    *pVal = OpeningBalance ;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeRate(double *pVal)  
{  
    double DesiredPayment = Payment;  
  
    for (Rate = 0.001; Rate < 28.0; Rate += 0.001)  
    {  
        Payment = Round(OpeningBalance * (Rate /   
         (1 - pow((1 + Rate), -Term))),2);  
  
        if (Payment >= DesiredPayment)  
            break;  
    }  
  
    *pVal = Rate;     
    return S_OK;  
}  
  
STDMETHODIMP CLoan::ComputeTerm(short *pVal)  
{  
    double DesiredPayment = Payment;  
    for (Term = 1; Term < 480 ; Term ++)  
    {  
        Payment = Round(OpeningBalance * (Rate /   
         (1 - pow((1 + Rate), -Term))),2);  
        if (Payment <= DesiredPayment)  
            break;  
    }  
    *pVal = Term;     
    return S_OK;  
}  
  
STDMETHODIMP CLoan::GetFirstPmtDistribution(double PmtAmt, double *Balance, double *PrinPortion, double *IntPortion, VARIANT_BOOL *pVal)  
{  
    *Balance = OpeningBalance;  
    GetNextPmtDistribution(PmtAmt, Balance, PrinPortion, IntPortion,   
      pVal);  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::GetNextPmtDistribution(double PmtAmt, double *Balance, double *PrinPortion, double *IntPortion, VARIANT_BOOL *pVal)  
{  
    *IntPortion = Round(*Balance * Rate, 2);  
    *PrinPortion = Round(PmtAmt - *IntPortion, 2);  
    *Balance = Round(*Balance - *PrinPortion, 2);  
  
    if (*Balance <= 0.0)  
        *pVal = FALSE;  
    else  
        *pVal = TRUE;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::get_RiskRating(BSTR *pVal)  
{  
    *pVal = (BSTR)RiskRating;  
    return S_OK;  
}  
  
STDMETHODIMP CLoan::put_RiskRating(BSTR newVal)  
{  
    RiskRating = newVal;  
    return S_OK;  
}  
static double Round(double value, short digits)   
{  
    double factor = pow(10, digits);  
    return floor(value * factor + 0.5)/factor;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Vystavení součástí COM v rozhraní .NET Framework](../../../docs/framework/interop/exposing-com-components.md)