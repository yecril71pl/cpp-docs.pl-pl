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
ms.openlocfilehash: d001cab897323d86d284958f322d155120a726a5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219757"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Ograniczenia parametrów typu ogólnego (C++/CLI)

W deklaracjach typu ogólnego lub metody można zakwalifikować parametr typu z ograniczeniami. Ograniczenie jest wymaganiem, że typy używane jako argumenty typu muszą być zgodne. Na przykład ograniczenie może oznaczać, że argument typu musi implementować określony interfejs lub dziedziczyć z określonej klasy.

Ograniczenia są opcjonalne; nieokreślanie ograniczenia parametru jest równoznaczne z ograniczeniami tego parametru do <xref:System.Object> .

## <a name="syntax"></a>Składnia

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parametry

*parametr typu*<br/>
Jeden z parametrów typu, który ma zostać ograniczony.

*Lista ograniczeń*<br/>
*Lista ograniczeń* jest rozdzielaną przecinkami listą specyfikacji ograniczeń. Lista może zawierać interfejsy, które mają być implementowane przez parametr typu.

Lista może również zawierać klasę. Dla argumentu typu, aby spełnić ograniczenie klasy bazowej, musi to być taka sama klasa jak ograniczenie lub dziedziczyć z ograniczenia.

Można także określić **gcnew ()** , aby wskazać, że argument typu musi mieć publiczny Konstruktor bez parametrów; lub **Klasa ref** wskazująca, że argument typu musi być typem referencyjnym, w tym dowolną klasą, interfejsem, delegatem lub typem tablicy; lub **Klasa wartości** wskazująca, że argument typu musi być typem wartości. Można określić dowolny typ wartości, z wyjątkiem dopuszczający wartości null \<T> .

Jako ograniczenie można także określić parametr generyczny. Argument typu dostarczony dla ograniczonego typu musi być lub pochodzić od typu ograniczenia. Jest to nazywane ograniczeniem typu owies.

## <a name="remarks"></a>Uwagi

Klauzula CONSTRAINT składa się z miejsca, w **którym** następuje parametr typu, dwukropek (**:**) i ograniczenie, które określa charakter ograniczenia w parametrze typu. **gdzie** jest kontekstowego słowa kluczowego; Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md) . Oddziel wiele klauzul **WHERE** spacją.

Ograniczenia są stosowane do parametrów typu w celu umieszczenia ograniczeń dotyczących typów, które mogą być używane jako argumenty dla typu ogólnego lub metody.

Ograniczenia klas i interfejsów określają, że typy argumentów muszą być lub dziedziczyć z określonej klasy lub zaimplementować określony interfejs.

Zastosowanie ograniczeń do typu ogólnego lub metody umożliwia kod w tym typie lub metodzie, aby wykorzystać znane funkcje typów z ograniczeniami. Na przykład można zadeklarować klasę generyczną w taki sposób, aby parametr typu implementuje `IComparable<T>` Interfejs:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

To ograniczenie wymaga, aby argument typu użyty dla `T` implementowania `IComparable<T>` w czasie kompilacji. Pozwala również na wywoływanie metod interfejsu, takich jak `CompareTo` . Nie jest konieczne rzutowanie na wystąpienie parametru typu w celu wywołania metod interfejsu.

Nie można wywołać metod statycznych w klasie argumentu typu za pomocą parametru typu; można je wywoływać tylko za pomocą rzeczywistego nazwanego typu.

Ograniczenie nie może być typem wartości, włącznie z wbudowanymi typami, takimi jak **`int`** lub **`double`** . Ponieważ typy wartości nie mogą mieć klas pochodnych, tylko jedna z nich może kiedykolwiek spełnić ograniczenie. W takim przypadku generyczne można napisać ponownie przy użyciu parametru typu zamienionego przez określony typ wartości.

Ograniczenia są wymagane w niektórych przypadkach, ponieważ kompilator nie zezwoli na użycie metod lub innych funkcji nieznanego typu, chyba że ograniczenia oznaczają, że nieznany typ obsługuje metody lub interfejsy.

Wiele ograniczeń dla tego samego parametru typu można określić na liście rozdzielanej przecinkami

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

W przypadku wielu parametrów typu należy użyć jednej klauzuli **WHERE** dla każdego parametru typu. Na przykład:

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

Aby podsumować, użyj ograniczeń w kodzie zgodnie z następującymi regułami:

- Jeśli na liście są wymienione wiele ograniczeń, ograniczenia mogą być wyświetlane w dowolnej kolejności.

- Ograniczenia mogą również być typami klas, takimi jak abstrakcyjne klasy bazowe. Jednak ograniczenia nie mogą być typami wartości ani zapieczętowanymi klasami.

- Ograniczenia nie mogą być parametrami typu, ale mogą zawierać parametry typu w otwartym typie skonstruowanym. Na przykład:

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

Poniższy przykład ilustruje używanie ograniczeń do wywoływania metod wystąpień w parametrach typu.

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

Gdy parametr typu generycznego jest używany jako ograniczenie, jest on nazywany ograniczeniem typu owies. Ograniczenia typu owies są przydatne, gdy funkcja członkowska z własnym parametrem typu musi ograniczyć ten parametr do parametru typu zawierającego.

W poniższym przykładzie, `T` jest ograniczeniem typu "owies" w kontekście `Add` metody.

Ograniczenia typu owies mogą być również używane w definicjach klas ogólnych. Użyteczność nieprawidłowych ograniczeń typu z klasami generycznymi jest ograniczona, ponieważ kompilator może założenie, że nic nie dotyczy ograniczenia typu wychodzącego, z wyjątkiem tego, że pochodzi od <xref:System.Object> . W scenariuszach, w których chcesz wymusić relację dziedziczenia między dwoma parametrami typu, należy używać wychodzących ograniczeń typu dla klas ogólnych.

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

## <a name="see-also"></a>Zobacz też

[Typy ogólne](generics-cpp-component-extensions.md)
