---
title: "Ograniczenia typu ogólnego parametrów (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: where
dev_langs: C++
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 01cd21e00cbf8947f5eb2ff8d2f578ab4912a03a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Ograniczenia parametrów typu ogólnego (C++/CLI)
W ogólnym typie lub metoda deklaracje kwalifikować się parametr typu z ograniczeniami. Ograniczenie jest wymaganie, które muszą spełniać typy używane jako argumentów typu. Na przykład ograniczenie może być czy argument typu musi implementować interfejs niektórych lub dziedziczyć po określonej klasy.  
  
 Ograniczenia są opcjonalne; nieokreślenie ograniczenia dla parametru jest odpowiednikiem ograniczający parametru do <xref:System.Object>.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
where type-parameter: constraint list  
```  
  
#### <a name="parameters"></a>Parametry  
 *Parametr typu*  
 Jeden z parametrów typu, aby być ograniczone.  
  
 *ograniczenie listy*  
 *ograniczenie listy* jest rozdzielaną przecinkami listą ograniczenia specyfikacji. Na liście mogą znajdować interfejsy powinny być implementowane przez parametr typu.  
  
 Listy mogą również obejmować klasy. Dla argumentu typu spełniać ograniczenie klasy podstawowej musi być taka sama klasa co ograniczenie lub pochodzić z ograniczenia.  
  
 Można również określić `gcnew()` wskazująca typ argumentu musi mieć publicznego konstruktora bez parametrów; lub `ref class` wskazująca argument typu musi być typem referencyjnym, łącznie z klasy, interfejsu, delegata lub typ tablicy; lub `value class` do wskazują, że argument typu musi być typem wartości. Wszystkie wartości typu z wyjątkiem Nullable\<T > można określić.  
  
 Można również określić parametr ogólny jako ograniczenia. Argumentu typu dostarczonego dla typu się, że są ograniczający musi być lub pochodzić od typu ograniczenia. Jest to ograniczenie bez typu.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula ograniczenia składa się z **gdzie** następuje parametr typu, dwukropek (**:**) i ograniczenia, które określa rodzaj ograniczenia dla parametru typu. **gdzie** jest słowem kluczowym kontekstowa, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji. Oddziel wiele **gdzie** klauzule się spacją.  
  
 Ograniczenia są stosowane do wpisz parametry, aby umieścić ograniczenia dotyczące typów, które mogą być używane jako argumentów typu ogólnego lub metody.  
  
 Ograniczenia klasy i interfejs określić, że typy argumentów musi być lub dziedziczą z klasy określonej lub implementować interfejs określony.  
  
 Stosowania ograniczeń typu ogólnego lub metody umożliwia kodu w tym typie lub metodzie mógł korzystać z funkcji znanych typów ograniczone. Na przykład można zadeklarować klasy ogólnej taki sposób, że parametr typu implementuje **IComparable\<T >** interfejsu:  
  
```  
// generics_constraints_1.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : IComparable<T>  
ref class List {};  
```  
  
 To ograniczenie wymaga argumentu typu dla `T` implementuje `IComparable<T>` w czasie kompilacji. Umożliwia także metody interfejsu, takich jak **CompareTo**, aby wywołać. Na wystąpienia parametru typu można wywoływać metod interfejsu niezbędna jest rzutowania.  
  
 Nie można wywołać metody statyczne klasy argument typu za pomocą parametru typu; można ich wywołać tylko za pośrednictwem rzeczywisty typ o nazwie.  
  
 Ograniczenie nie może być typem wartości, takich jak tym wbudowane typy `int` lub **podwójne**. Ponieważ typów wartości nie może mieć pochodne klasy, tylko jedna klasa kiedykolwiek będą mogli spełniać ograniczenie. W takim przypadku ogólnego może ulegną z parametrem typu zastąpiony przez typ określonej wartości.  
  
 Ponieważ kompilator nie zezwala na korzystanie z metod lub innych funkcji nieznanego typu, chyba że ograniczenia oznacza, że nieznany typ obsługuje metod lub interfejsów w niektórych przypadkach wymagane są ograniczenia.  
  
 Można określić wiele ograniczeń dla tego samego parametru typu w postaci listy rozdzielanej przecinkami  
  
```  
// generics_constraints_2.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
generic <typename T>  
where T : List<T>, IComparable<T>  
ref class List {};  
```  
  
 Wiele parametrów typu, za pomocą jednego **gdzie** klauzula dla każdego parametru typu. Na przykład:  
  
```  
// generics_constraints_3.cpp  
// compile with: /c /clr  
using namespace System;  
using namespace System::Collections::Generic;  
  
generic <typename K, typename V>  
   where K: IComparable<K>  
   where V: IComparable<K>  
ref class Dictionary {};  
```  
  
 Podsumowując, użyj ograniczenia w kodzie zgodnie z następującymi zasadami:  
  
-   Jeśli nie są wyświetlane wiele ograniczeń, ograniczenia mogą być wyświetlone w dowolnej kolejności.  
  
-   Ograniczenia mogą być również typy klas, takich jak abstrakcyjnych klas podstawowych. Jednak ograniczenia nie może być typów wartości lub zapieczętowane klasy.  
  
-   Same ograniczenia nie może być parametrami typu, ale wymagają one parametrów typu w skonstruowanego typu otwartego. Na przykład:  
  
    ```  
    // generics_constraints_4.cpp  
    // compile with: /c /clr  
    generic <typename T>  
    ref class G1 {};  
  
    generic <typename Type1, typename Type2>  
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter  
    ref class G2{};  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, za pomocą ograniczenia do wywołania metody wystąpienia dotyczące parametrów typu.  
  
```  
// generics_constraints_5.cpp  
// compile with: /clr  
using namespace System;  
  
interface class IAge {  
   int Age();  
};  
  
ref class MyClass {  
public:  
   generic <class ItemType> where ItemType : IAge   
   bool isSenior(ItemType item) {  
      // Because of the constraint,  
      // the Age method can be called on ItemType.  
      if (item->Age() >= 65)   
         return true;  
      else  
         return false;  
   }  
};  
  
ref class Senior : IAge {  
public:  
   virtual int Age() {  
      return 70;  
   }  
};  
  
ref class Adult: IAge {  
public:  
   virtual int Age() {  
      return 30;  
   }  
};  
  
int main() {  
   MyClass^ ageGuess = gcnew MyClass();  
   Adult^ parent = gcnew Adult();  
   Senior^ grandfather = gcnew Senior();  
  
   if (ageGuess->isSenior<Adult^>(parent))  
      Console::WriteLine("\"parent\" is a senior");  
   else  
      Console::WriteLine("\"parent\" is not a senior");  
  
   if (ageGuess->isSenior<Senior^>(grandfather))  
      Console::WriteLine("\"grandfather\" is a senior");  
   else  
      Console::WriteLine("\"grandfather\" is not a senior");  
}  
```  
  
```Output  
"parent" is not a senior  
"grandfather" is a senior  
```  
  
## <a name="example"></a>Przykład  
 Parametr typu ogólnego jest używany jako ograniczenie, jest nazywany ograniczenia bez typu. Ograniczenia typu naked są przydatne, gdy funkcji członkowskiej z własną parametr typu ma ograniczenie parametru typu parametru typu zawierającego.  
  
 W poniższym przykładzie T jest ograniczenia typu naked w kontekście metody Add.  
  
 Ograniczenia typu naked można również w definicji klasy ogólnej. Przydatność ograniczenia typu naked z klasami ogólnego są ograniczone, ponieważ kompilator można założyć, nie ma ograniczenia typu naked z tą różnicą, że pochodzi od <xref:System.Object>. Użyj typu bez ograniczenia klasy ogólne w scenariuszach, w których ma zostać wymuszone relację dziedziczenia między dwoma parametrami typu.  
  
```  
// generics_constraints_6.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct List {  
   generic <class U>  
   where U : T  
   void Add(List<U> items)  {}  
};  
  
generic <class A, class B, class C>  
where A : C  
ref struct SampleClass {};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)