---
title: Použití odchylky v rozhraní pro obecné kolekce (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 66a1eac33d5f715f52bd83c43bac4452df41aabd
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122354"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Použití odchylky v rozhraní pro obecné kolekce (C#)
Kovariantní rozhraní umožňuje její metody k vrácení více odvozené typy než procesory zadané v rozhraní. Rozhraní kontravariantní umožňuje její metody přijímají parametry méně odvozené typy než platformám zadaným v rozhraní.  
  
 V rozhraní .NET Framework 4, stala několik existujících rozhraní kovariantního a kontravariantního. Patří mezi ně <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.IComparable%601>. To umožňuje znovu použít metody, které pracují s obecné kolekce základních typů pro kolekce odvozené typy.  
  
 Seznam variantních rozhraní v rozhraní .NET Framework najdete v tématu [odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Převádění obecných kolekcí  
 Následující příklad ukazuje výhody podpory Kovariance v <xref:System.Collections.Generic.IEnumerable%601> rozhraní. `PrintFullName` Metoda přijímá kolekce `IEnumerable<Person>` typ jako parametr. Ale můžete použít pro kolekce `IEnumerable<Employee>` typu, protože `Employee` dědí `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a>Porovnání obecné kolekce  
 Následující příklad ukazuje výhody podpory kontravariance v <xref:System.Collections.Generic.IComparer%601> rozhraní. `PersonComparer` Implementuje třída `IComparer<Person>` rozhraní. Ale můžete znovu použít tuto třídu pro porovnání sekvence objektů `Employee` typu, protože `Employee` dědí `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Odchylky obecných rozhraní (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
