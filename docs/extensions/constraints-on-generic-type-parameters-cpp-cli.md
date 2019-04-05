---
title: Ograniczenia parametrów typu ogólnego (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: 6eefb6a7d888a031f6ff7f88d08da4d67a4dc8c3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035038"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Ograniczenia parametrów typu ogólnego (C++/CLI)

W ogólnym typie lub deklaracje metody możesz skorzystać z parametrem typu ograniczenia. Ograniczenie to wymaganie, które muszą spełniać typy używane jako argumenty typu. Na przykład może być ograniczenie, że argument typu musi implementować niektórych interfejsu lub dziedziczyć z określonej klasy.

Ograniczenia są opcjonalne; Brak określenia ograniczenie dotyczące parametru jest odpowiednikiem ograniczając tego parametru, aby <xref:System.Object>.

## <a name="syntax"></a>Składnia

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parametry

*Parametr typu*<br/>
Jeden z parametrów typu, aby być ograniczone.

*Lista ograniczeń*<br/>
*Lista ograniczeń* jest rozdzielana przecinkami lista ograniczenia specyfikacji. Na liście mogą znajdować interfejsy do zaimplementowania przez parametr typu.

Lista może również zawierać klasę. Dla argumentu typu spełniać ograniczenie klasy bazowej musi być taka sama klasa co ograniczenia lub pochodzić od ograniczenia.

Można również określić **gcnew()** do wskazania, argument typu musi mieć publicznego konstruktora bez parametrów; lub **klasy referencyjnej** do wskazania, argument typu musi być typem referencyjnym, łącznie z dowolnej klasy interfejsu, delegata lub tablicy typu; lub **klasę wartości** aby wskazać typ argumentu musi być typem wartości. Wszystkie wartości typu z wyjątkiem Nullable\<T > może być określony.

Można również określić parametr ogólny jako ograniczenie. Typ podany argument dla typu, są ograniczając musi być lub pochodzić od typu ograniczenia. Jest to ograniczenie typu "naked".

## <a name="remarks"></a>Uwagi

Klauzula constraint składa się z **gdzie** następuje dwukropek, parametr typu (**:**) i ograniczenia, które określa rodzaj ograniczenia dla parametru typu. **gdzie** jest kontekstowe słowo kluczowe; zobacz [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji. Oddziel wiele **gdzie** klauzule ze spacją.

Ograniczenia są stosowane do parametrów, aby umieścić ograniczenia na typy, które mogą być używane jako argumenty typu ogólnego lub metody typu.

Ograniczenia klasy i interfejs określić typy argumentów musi być lub dziedziczą z klasy określonej lub implementacji określonego interfejsu.

Stosowanie ograniczeń typu ogólnego lub metody umożliwia kodu w tym typie lub metodzie, aby móc korzystać z funkcji znanych typów ograniczone. Na przykład, możesz zadeklarować klasy ogólnej taki sposób, że parametr typu implementuje `IComparable<T>` interfejsu:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

To ograniczenie wymaga argumentu typu dla `T` implementuje `IComparable<T>` w czasie kompilacji. Umożliwia także metody interfejsu, takich jak `CompareTo`, ma zostać wywołana. Brak rzutowania pozwala na potrzeby wystąpienie parametru typu wywoływać metod interfejsu.

Nie można wywołać metody statycznej w klasie argument typu za pomocą parametru typu; one może być wywoływana tylko za pośrednictwem rzeczywisty typ o nazwie.

Ograniczenie nie może być typem wartości, w tym wbudowanych typów, takich jak **int** lub **double**. Ponieważ typy wartości nie może mieć pochodne klasy, tylko jedną klasę nigdy nie będzie mogła spełniać ograniczenie. W takiej sytuacji można inaczej ogólnego z parametrem typu zastąpiony przez typ określonej wartości.

Ograniczenia są wymagane w niektórych przypadkach, ponieważ kompilator nie pozwoli na korzystanie z metod lub innych funkcji nieznanego typu, chyba że ograniczenia oznaczają, że nieznany typ obsługuje metody lub interfejsów.

Można określić wiele ograniczeń dla tego samego parametru typu na liście rozdzielanej przecinkami

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

Z wieloma parametrami typu, użyj jednej **gdzie** klauzulę dla każdego parametru typu. Na przykład:

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

Aby podsumować, użyj ograniczeń w kodzie, zgodnie z następującymi zasadami:

- Jeśli na liście wielu ograniczeń ograniczenia może być wyświetlane w dowolnej kolejności.

- Ograniczenia mogą być również typy klas, takie jak abstrakcyjnych klas bazowych. Typy wartości lub klasach zapieczętowanych nie można jednak ograniczenia.

- Same ograniczenia nie może być parametrami typu, ale może pociągać za sobą parametrów typu w ramach skonstruowanego typu otwartego. Na przykład:

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, za pomocą ograniczeń do wywołania metody wystąpienia w parametrach typu.

```cpp
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

Parametr typu ogólnego jest używany jako ograniczenie, jest nazywany ograniczenia typu "naked". Ograniczenia typu "naked" są przydatne, gdy trzeba ograniczyć tego parametru na parametr typu dla typu zawierającej funkcji składowej z parametrem typu.

W poniższym przykładzie `T` ograniczenie typu "naked" w kontekście `Add` metody.

Ograniczenia typu "naked" można również w definicji klasy ogólnej. Użyteczność ograniczenia typu "naked" przy użyciu klas ogólnych jest ograniczona, ponieważ kompilator może przyjąć nie ma ograniczenia typu "naked", z tą różnicą, że pochodzi od klasy <xref:System.Object>. Użyj ograniczeń typu "naked" w klasach ogólnych w scenariuszach, w których ma zostać wymuszone relacje dziedziczenia między dwa parametry typu.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Typy ogólne](generics-cpp-component-extensions.md)