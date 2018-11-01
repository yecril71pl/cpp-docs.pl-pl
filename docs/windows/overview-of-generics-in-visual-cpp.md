---
title: Przegląd typów ogólnych w języku C + +/ CLI
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 1105025ebebdfcbce723505747f6677674c04334
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655172"
---
# <a name="overview-of-generics-in-ccli"></a>Przegląd typów ogólnych w języku C + +/ CLI

Typy ogólne są obsługiwane przez środowisko uruchomieniowe języka wspólnego typami z parametrami. Typ sparametryzowany jest typem, która jest zdefiniowana za pomocą parametru nieznany typ, który jest określony, gdy ogólnego jest używany.

## <a name="why-generics"></a>Dlaczego ogólne?

Język C++ obsługuje szablony i zarówno i typy ogólne obsługuje sparametryzowanych typów do tworzenia klas typizowaną kolekcją. Jednak Szablony zapewniają parametryzacji w czasie kompilacji. Nie można odwoływać się do zestawu zawierającego definicji szablonu i utworzyć nowe specjalizacje szablonu. Po skompilowaniu wyspecjalizowane szablon wygląda jak inne klasy lub metody. Z kolei typy ogólne są emitowane w kodzie MSIL jako typ sparametryzowany znane przez środowisko uruchomieniowe jako typ sparametryzowany; Kod źródłowy, który odwołuje się do zestawu zawierającego typ ogólny, można utworzyć specjalizacje typu ogólnego. Aby uzyskać więcej informacji na porównaniu standardowych szablonów języka C++ i typami ogólnymi zobacz [typy ogólne i szablony (C + +/ CLI)](../windows/generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Funkcje ogólne i typów

Typy klas, tak długo, jak są one zarządzane typy, może być ogólny. Na przykład może być `List` klasy. Typ obiektu, na liście będzie parametru typu. W razie potrzeby możesz `List` klasy dla wielu różnych typów obiektów, zanim możliwe, że używasz typów ogólnych `List` przyjmującej `System::Object` jako typ elementu. Jednak, Zezwalaj na dowolny obiekt (w tym obiekty niewłaściwego typu) ma być używany na liście. Takie listy będzie wywoływana klasy kolekcji bez typu. W najlepszym możesz sprawdzić typ w czasie wykonywania i zgłosić wyjątek. Lub może być używany jako szablon, który spowoduje utratę jego jakość ogólnego raz kompilowane do zestawu. Konsumenci zestawu nie może utworzyć własne specjalizacje szablonu. Typy ogólne pozwalają tworzyć klasy typizowaną kolekcją, załóżmy, że `List<int>` (Odczyt, jak "Lista int") i `List<double>` ("Lista podwójnej") nie który wygeneruje błąd w czasie kompilacji, jeśli próbowano put typ, który został kolekcji przeznaczona do akceptowania pod kontrolą typów Kolekcja. Ponadto te typy rodzajowe po pozostają są one kompilowane.

Opis składni klasy ogólne można znaleźć w [klasy ogólne (C + +/ CLI)](../windows/generic-classes-cpp-cli.md). Nowy obszar nazw <xref:System.Collections.Generic>, wprowadza zestaw typów sparametryzowanych kolekcji, w tym <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.LinkedList%601>.

Zarówno wystąpienia i elementów członkowskich klasy statycznej, delegatów i funkcje globalne mogą być również ogólne. Funkcje ogólne może być konieczne, jeśli parametry funkcji są nieznanego typu lub jeśli sama funkcja należy skontaktować się z typów ogólnych. W wielu przypadkach gdzie `System::Object` były używane w przeszłości jako parametru dla nieznany typ obiektu, parametr typu ogólnego może być używany zamiast tego, co zapewnia więcej kod bezpiecznego typu. Każda próba przekazania w typie, że funkcja nie jest przeznaczone dla zostanie oznaczony jako błąd w czasie kompilacji. Za pomocą `System::Object` jako parametru funkcji, nieumyślne przekazywanie obiektu funkcji nie ma dotyczyć nie można wykryć i trzeba byłoby rzutowania nieznany typ obiektu określonego typu w treści funkcji, a konto możliwość InvalidCastException. Za pomocą zwykłego kodu próby przekazania obiektu do funkcji spowoduje, że konflikt typu, dzięki czemu gwarantuje ma niepoprawny typ treści funkcji.

Te same korzyści mają zastosowanie do klasy kolekcji, w oparciu o typy ogólne. Użyj klasy kolekcji w przeszłości `System::Object` do przechowywania elementów w kolekcji. Wstawianie obiektów tego typu, który kolekcji nie jest przeznaczone dla nie została oflagowana, w czasie kompilacji, a często nawet w przypadku, gdy obiekty zostały wstawione. Zazwyczaj obiekt może być rzutowany innego typu dostępie w kolekcji. Tylko wtedy, gdy Rzutowanie nie powiodło się. nieoczekiwany typ można wykryć. Typy ogólne rozwiązuje ten problem w czasie kompilacji został określony poprzez wykrycie wszelki kod, który wstawia typ, który nie odpowiada (lub niejawnie konwertowane) parametr typu kolekcji ogólnej.

Opis składni, zobacz [funkcje ogólne (C + +/ CLI)](../windows/generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminologia używana za pomocą typów ogólnych

### <a name="type-parameters"></a>Parametry typów

Deklaracji ogólnej zawiera co najmniej jeden nieznany typ znany jako *parametry typu*. Parametry typu są podane nazwy, który oznacza typ w treści deklaracji ogólnej. Parametr typu jest używany jako typ w treści deklaracji ogólnej. Ogólny deklaracji pod kątem `List<T>` zawiera parametr typu T.

### <a name="type-arguments"></a>Argumenty typu

*Argument typu* jest rzeczywisty typ używać zamiast parametru typu ogólnego jest przeznaczone dla określonego typu lub typów. Na przykład **int** jest argumentem typu w `List<int>`. Typy wartości i uchwyt to jedyne typy, które są dozwolone w jako argument typu ogólnego.

### <a name="constructed-type"></a>Skonstruowany typ

Typ skonstruowany z typu generycznego jest określany jako *skonstruowany typ*. Typ, nie są w pełni określona, takich jak `List<T>` jest *Otwórz skonstruowanego typu*; w pełni określona, takie jak typ `List<double>,` jest *zamknięte skonstruowanego typu* lub *wyspecjalizowane typu* . Otwórz typy utworzone mogą być używane w definicji innych typów ani metod ogólnych i nie może być w pełni określona do momentu ogólnego otaczający jest określony. Na przykład Oto Użyj skonstruowanego typu otwartego jako klasę bazową dla ogólnej:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Ograniczenia

Ograniczenie jest ograniczenie typów, które mogą być używane jako parametr typu. Na przykład danej klasy ogólnej może akceptować tylko klasy, które dziedziczą z określonej klasy lub implementacji określonego interfejsu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Typy odwołań i typy wartości

Obsługuje typy i wartości może służyć jako argumentów typu. W ogólnych definicji, w którym typ mogą być używane, składnia jest typy odwołań. Na przykład `->` operator jest używany do dostęp do elementów członkowskich typu parametru typu, czy typ ostatecznie używany jest typem referencyjnym lub typem wartości. Jeśli typ wartości jest używana jako argument typu, środowisko uruchomieniowe generuje kod, który używa typów wartości bezpośrednio, bez konwersja boxing typów wartości.

Korzystając z typem referencyjnym jako argument typu ogólnego, należy użyć składni dojście. Podczas korzystania z typu wartości jako argument typu ogólnego, nazwa typu korzystać bezpośrednio.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>Parametry typów

Parametry typu rodzajowego klasy są traktowane jak innych identyfikatorów. Ponieważ typ nie jest znany, istnieją jednak ograniczenia związane z ich użyciem. Na przykład nie można użyć elementów członkowskich i metod klasy parametr typu, chyba że parametr typu jest znany do obsługi tych elementów członkowskich. Oznacza to aby uzyskiwanie dostępu do członka za pomocą parametru typu, należy dodać typ, który zawiera element członkowski do listy ograniczenia parametru typu.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

Te ograniczenia mają zastosowanie również operatorów. Nie można używać parametru typu ogólnego nieograniczonego `==` i `!=` operatory do porównywania dwóch wystąpień z parametrem typu, w przypadku, gdy typ nie obsługuje tych operatorów. Te testy są niezbędne do typów ogólnych, ale nie dla szablonów, ponieważ może można wyspecjalizować typy ogólne w czasie wykonywania za pomocą dowolnej klasy spełniającego ograniczenia, gdy jest za późno, aby sprawdzić, czy użycie nieprawidłowych członków.

Domyślne wystąpienie parametru typu można tworzyć przy użyciu `()` operatora. Na przykład:

`T t = T();`

gdzie `T` jest parametrem typu w definicji klasy lub metody rodzajowe, inicjuje zmienną na wartość domyślną. Jeśli `T` jest klasą referencyjną, będzie on wskaźnikiem typu null; Jeśli `T` jest klasą wartość obiektu jest inicjowane od zera. Jest to nazywane *domyślny inicjator*.

## <a name="see-also"></a>Zobacz też

[Typy ogólne](../windows/generics-cpp-component-extensions.md)