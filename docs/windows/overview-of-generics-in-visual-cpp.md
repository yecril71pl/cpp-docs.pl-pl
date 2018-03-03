---
title: "Przegląd typów ogólnych w programie Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5082f603c64e796ef369044e3586ae5bfe85605a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-generics-in-visual-c"></a>Przegląd typów ogólnych w Visual C++
Typy ogólne są obsługiwane przez środowisko uruchomieniowe języka wspólnego typy z parametrami. Sparametryzowany typ jest typem, który jest zdefiniowana z parametrem nieznany typ określona po ogólnego jest używany.  
  
## <a name="why-generics"></a>Dlaczego ogólne?  
 C++ obsługuje szablony i jednocześnie szablonów i ogólne obsługuje typy z parametrami można utworzyć klasy typu kolekcji. Jednak Szablony zapewniają parametryzacja kompilacji. Nie można odwołanie do zestawu zawierającego definicję szablonu i utworzyć nowe specjalizacji szablonu. Po skompilowany, szablon specjalne wygląda jak inne klasy lub metody. Z kolei wysyłanego ogólne jako sparametryzowany typ wiadomo przez środowisko uruchomieniowe sparametryzowany typ; MSIL Kod źródłowy, który odwołuje się do zestawu zawierającego typ rodzajowy można utworzyć specjalizacje typu ogólnego. Aby uzyskać więcej informacji na porównaniu szablonów Visual C++ i typami ogólnymi, zobacz [typy ogólne i szablony (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
## <a name="generic-functions-and-types"></a>Funkcje ogólne i typów  
 Typy klas tak długo, jak są one typy zarządzane, może być rodzajowy. Na przykład może być `List` klasy. Typ obiektu na liście będzie parametru typu. Jeśli potrzebne są `List` klasy dla wielu różnych typów obiektów, przed ogólne, być może użyto `List` pobierającej **System::Object** jako typ elementu. Ale które umożliwiałyby dowolnego obiektu (w tym obiektów niewłaściwego typu) do użycia na liście. Takie listy będzie można wywołać klasy bez typu kolekcji. Można w najlepszym Sprawdź typ w czasie wykonywania i zgłosić wyjątek. Lub może być używany jako szablon, który spowoduje utratę jego rodzajowe raz skompilowany w zestawie. Konsumenci używanego zestawu nie może utworzyć własne specjalizacji szablonu. Ogólne pozwala na tworzenie klasy typizowaną kolekcją, powiedz `List<int>` (do odczytu jako"int") i `List<double>` ("Lista double") która powoduje wygenerowanie błąd kompilacji, jeśli próbowano umieść typ, który był kolekcji nie umożliwia akceptowanie do typu Kolekcja. Ponadto te typy pozostają ogólnego po są one kompilowane.  
  
 Opis składni klas rodzajowych można znaleźć w [klasy ogólne (C + +/ CLI)](../windows/generic-classes-cpp-cli.md) `.` nowej przestrzeni nazw, <xref:System.Collections.Generic>, wprowadzono nowy zestaw typów sparametryzowane kolekcji, w tym <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601>i <xref:System.Collections.Generic.LinkedList%601>.  
  
 Zarówno wystąpienia i klasy statycznej funkcji Członkowskich delegatów i funkcje globalne mogą być również ogólne. Funkcje ogólne może być konieczne, jeśli parametry funkcji jest nieznanego typu lub jeśli sama funkcja należy skontaktować się z typów ogólnych. W wielu przypadkach gdy **System::Object** mogą zostać wykorzystane w przeszłości jako parametru dla nieznany typ obiektu, parametru typu ogólnego może być używany zamiast tego, co zapewnia więcej bezpieczny kod. Każda próba przekazania w typie funkcji nie jest przeznaczone dla zostanie oznaczony jako błąd w czasie kompilacji. Przy użyciu **System::Object** jako parametr funkcji przypadkowej przekazywanie obiektu funkcji nie mają dotyczyć nie można wykryć i konieczne będzie można rzutować typu nieznanego obiektu określonego typu w treść funkcji, a konto umożliwiające invalidcastexception —. Z ogólnego kod próba przekazania obiektu funkcji spowoduje, że konflikt typu tak treść funkcji jest gwarantowane ma poprawnego typu.  
  
 Te same korzyści mają zastosowanie do klasy kolekcji oparte na ogólne. Klasy kolekcji w ciągu ostatnich użyje **System::Object** do przechowywania elementów w kolekcji. Wstawiania obiektów typu kolekcji nie jest przeznaczone dla został nie oflagowane w czasie kompilacji i często, nawet w przypadku, gdy obiekty zostały wstawione. Zwykle czy można rzutować obiektu do innego typu dostępie w kolekcji. Tylko wtedy, gdy Rzutowanie nie powiodło się. nieoczekiwany typ można wykryć. Typy ogólne rozwiązuje ten problem w czasie kompilacji został określony poprzez wykrycie żadnego kodu, która wstawia typu, który nie odpowiada (lub niejawnie konwertowane) parametru typu ogólnego kolekcji.  
  
 Aby uzyskać opis składni, zobacz [funkcje ogólne (C + +/ CLI)](../windows/generic-functions-cpp-cli.md).  
  
## <a name="terminology-used-with-generics"></a>Terminologia używana z ogólnymi  
  
##### <a name="type-parameters"></a>Parametry typów  
 Deklaracja ogólna zawiera co najmniej jeden nieznany typ znany jako *parametry typu*. Parametry typu podano nazwę, która oznacza typu w treści deklaracja ogólna. Parametr typu jest używany jako typ w treści deklaracja ogólna. Deklaracja ogólna dla listy < T\> zawiera parametr typu T.  
  
##### <a name="type-arguments"></a>Argumenty typów  
 *Argument typu* jest rzeczywisty typ użyto zamiast tego parametru typu ogólnego jest przeznaczone do określonego typu lub typy. Na przykład `int` jest argumentem typu w `List<int>`. Typy wartości i typ dojścia są tylko typy w można użyć jako argumentu typu ogólnego.  
  
##### <a name="constructed-type"></a>Utworzony typ  
 Typ utworzone na podstawie typu ogólnego jest określany jako *skonstruować typu*. Typem nie pełni określony, takich jak `List<T>` jest *Otwórz skonstruowanego typu*; pełni określony, takie jak typ `List<double>,` jest *zamknięte skonstruowanego typu* lub *specjalizowany typu* . Otwórz typy utworzone mogą być używane w definicji innych typów ogólnych lub metody i nie może być całkowicie określona do momentu otaczającej ogólnego jest określona. Na przykład następujące jest użycie typu otwartego skonstruowane jako klasę podstawową dla ogólnego:  
  
 `// generics_overview.cpp`  
  
 `// compile with: /clr /c`  
  
 `generic <typename T>`  
  
 `ref class List {};`  
  
 `generic <typename T>`  
  
 `ref class Queue : public List<T> {};`  
  
##### <a name="constraint"></a>Ograniczenia  
 Ograniczenie jest ograniczenie typy, które mogą być używane jako parametr typu. Na przykład danej klasy ogólnej może zaakceptować tylko klasy, które dziedziczą z klasy określonej lub wykonania określonego interfejsu. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
## <a name="reference-types-and-value-types"></a>Typy odwołań i typów wartości  
 Typy dojść i typów wartości mogą zostać użyte jako argumentów typu. W definicji ogólne, w którym typ może być używany, składnia jest typy referencyjne. Na przykład  **->**  operator umożliwia dostęp do elementów członkowskich typu parametru typu, czy typ ostatecznie używany jest typem referencyjnym lub typem wartości. W przypadku typu wartości jako argument typu środowiska uruchomieniowego generuje kod, który korzysta z typów wartości bezpośrednio, bez konwersja boxing typów wartości.  
  
 Korzystając z typem referencyjnym jako argumentu typu ogólnego, należy użyć składni dojścia. Korzystając z typem wartości jako argumentu typu ogólnego, nazwa typu korzystać bezpośrednio.  
  
 `// generics_overview_2.cpp`  
  
 `// compile with: /clr`  
  
 `generic <typename T>`  
  
 `ref class GenericType {};`  
  
 `ref class ReferenceType {};`  
  
 `value struct ValueType {};`  
  
 `int main() {`  
  
 `GenericType<ReferenceType^> x;`  
  
 `GenericType<ValueType> y;`  
  
 `}`  
  
## <a name="type-parameters"></a>Parametry typów  
 Parametrów typu w klasie rodzajowej są traktowane jak innych identyfikatorów. Ponieważ typ nie jest znany, istnieją jednak ograniczenia związane z ich użyciem. Na przykład nie można używać elementów członkowskich i metod klasy parametr typu, chyba, że parametr typu jest znany do obsługi tych elementów członkowskich. Oznacza to aby uzyskiwanie dostępu do członka za pomocą parametru typu, należy dodać typ, który zawiera element do listy ograniczenia parametru typu.  
  
 `// generics_overview_3.cpp`  
  
 `// compile with: /clr`  
  
```  
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
  
 Ograniczenia te dotyczą także operatorów. Nie można używać parametru typu ogólnego nieograniczonego `==` i `!=` operatorów, aby porównać dwa wystąpienia parametru typu w przypadku, gdy typ nie obsługuje następujące operatory. Te testy są niezbędne dla typów ogólnych, ale nie dla szablonów, ponieważ może być specjalizowany typy ogólne w czasie wykonywania z dowolnej klasy spełniającego ograniczenia, gdy jest za późno do sprawdzenia użycie nieprawidłowych członków.  
  
 Można tworzyć przy użyciu domyślnego wystąpienia parametru typu `()` operatora. Na przykład:  
  
 `T t = T();`  
  
 gdzie `T` jest parametrem typu w definicji klasy lub metody ogólne, inicjuje zmiennej na wartość domyślną. Jeśli `T` jest klasa ref, będzie on wskaźnika o wartości null; Jeśli `T` jest klasą wartości obiektu ustawiana jest wartość zero. Ta metoda jest wywoływana *domyślne inicjatora*.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)