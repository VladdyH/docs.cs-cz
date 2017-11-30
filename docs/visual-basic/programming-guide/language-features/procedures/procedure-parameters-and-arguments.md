---
title: Parametry a argumenty procedury (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="21f22-102">Parametry a argumenty procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21f22-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="21f22-103">Ve většině případů musí procedury některé informace o v případech, ve kterých byla volána.</span><span class="sxs-lookup"><span data-stu-id="21f22-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="21f22-104">Procedury, která provádí opakovaných nebo sdíleného úlohy používá různé informace pro každé volání.</span><span class="sxs-lookup"><span data-stu-id="21f22-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="21f22-105">Tyto informace se skládá z proměnné, konstanty a výrazy, které se předávají k postupu při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="21f22-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="21f22-106">A *parametr* představuje hodnotu, která procedura očekává, že můžete zadat při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="21f22-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="21f22-107">Deklarace procedury definuje jeho parametry.</span><span class="sxs-lookup"><span data-stu-id="21f22-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="21f22-108">Můžete definovat procedura se žádné parametry, parametr jeden nebo více než jeden.</span><span class="sxs-lookup"><span data-stu-id="21f22-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="21f22-109">Se označuje jako součást definice procedury, která určuje parametry *seznam parametrů*.</span><span class="sxs-lookup"><span data-stu-id="21f22-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="21f22-110">*Argument* představuje hodnotu zadáte parametr postupu při voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="21f22-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="21f22-111">Volání kódu poskytuje argumenty, když se volá proceduru.</span><span class="sxs-lookup"><span data-stu-id="21f22-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="21f22-112">Část volání procedury, která určuje argumenty, které se nazývá *seznam argumentů*.</span><span class="sxs-lookup"><span data-stu-id="21f22-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="21f22-113">Následující obrázek znázorňuje kód volání postup `safeSquareRoot` ze dvou různých míst.</span><span class="sxs-lookup"><span data-stu-id="21f22-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="21f22-114">První volání předá hodnotu proměnné `x` (4.0) na parametr `number`a návratovou hodnotu v `root` (2.0) je přiřazen k proměnné `y`.</span><span class="sxs-lookup"><span data-stu-id="21f22-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="21f22-115">Druhé volání předá hodnotu literálu 9.0 k `number`a přiřadí návratovou hodnotu (3.0) k proměnné `z`.</span><span class="sxs-lookup"><span data-stu-id="21f22-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="21f22-116">![Grafický diagram předání argument na parametr](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="21f22-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="21f22-117">Předávání argument na parametr</span><span class="sxs-lookup"><span data-stu-id="21f22-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="21f22-118">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="21f22-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="21f22-119">Typ dat parametru</span><span class="sxs-lookup"><span data-stu-id="21f22-119">Parameter Data Type</span></span>  
 <span data-ttu-id="21f22-120">Definovat datový typ pro parametr pomocí `As` klauzuli v jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="21f22-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="21f22-121">Například následující funkce přijme řetězce a celé číslo.</span><span class="sxs-lookup"><span data-stu-id="21f22-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="21f22-122">Pokud kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off,` `As` klauzule je volitelné, s tím rozdílem, že pokud žádné jeden parametr používá ji, všechny parametry musí používat.</span><span class="sxs-lookup"><span data-stu-id="21f22-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="21f22-123">Pokud kontrola typu `On`, `As` klauzule je vyžadována pro všechny parametry procedur.</span><span class="sxs-lookup"><span data-stu-id="21f22-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="21f22-124">Pokud kód volání očekává, zadejte argument s datovým typem, který se liší od odpovídajícího parametru, jako například `Byte` k `String` parametru, je nutné provést s některou z následujících:</span><span class="sxs-lookup"><span data-stu-id="21f22-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="21f22-125">Zadejte pouze argumenty s typy dat, které rozšíří na datový typ parametru;</span><span class="sxs-lookup"><span data-stu-id="21f22-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="21f22-126">Nastavit `Option Strict Off` umožňuje implicitní zužující převody; nebo</span><span class="sxs-lookup"><span data-stu-id="21f22-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="21f22-127">Explicitně převést na datový typ pomocí klíčového slova převodu.</span><span class="sxs-lookup"><span data-stu-id="21f22-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="21f22-128">Parametry typu</span><span class="sxs-lookup"><span data-stu-id="21f22-128">Type Parameters</span></span>  
 <span data-ttu-id="21f22-129">A *obecný postup* definuje také nejméně jeden *parametry typu* kromě jeho normální parametry.</span><span class="sxs-lookup"><span data-stu-id="21f22-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="21f22-130">Obecný postup umožňuje kód volání předat různé datové typy pokaždé, když ho volá proceduru, takže ho můžete přizpůsobit datové typy požadavků na jednotlivých volání.</span><span class="sxs-lookup"><span data-stu-id="21f22-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="21f22-131">V tématu [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="21f22-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f22-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="21f22-132">See Also</span></span>  
 [<span data-ttu-id="21f22-133">Postupy</span><span class="sxs-lookup"><span data-stu-id="21f22-133">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="21f22-134">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="21f22-134">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="21f22-135">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="21f22-135">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="21f22-136">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="21f22-136">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="21f22-137">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="21f22-137">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="21f22-138">Postupy: definování parametru pro proceduru</span><span class="sxs-lookup"><span data-stu-id="21f22-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="21f22-139">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="21f22-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="21f22-140">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="21f22-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="21f22-141">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="21f22-141">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="21f22-142">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21f22-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
