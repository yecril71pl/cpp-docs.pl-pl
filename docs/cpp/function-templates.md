---
title: Szablony funkcji
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: f2caf70dd90e76c7bc4f20ea4bf34845b343efc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179747"
---
# <a name="function-templates"></a>Szablony funkcji

Szablony klas definiują rodzinę powiązanych klas, które są oparte na argumentach typu przekazywanych do klasy podczas tworzenia jej wystąpienia. Szablony funkcji są podobne do szablonów klas, ale definiują rodzinę funkcji. Dzięki szablonom funkcji, możesz określić zestaw funkcji, które są oparte na tym samym kodzie, ale działają na różnych typach lub klasach. Następujący szablon funkcji zamienia dwa elementy:

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

Ten kod definiuje rodzinę funkcji, które zamieniają wartości argumentów. Z tego szablonu można generować funkcje, które zastąpią typy **int** i **Long** , a także typy zdefiniowane przez użytkownika. `MySwap` będzie zamieniać nawet klasy, jeśli w klasie został poprawnie zdefiniowany konstruktor kopiujący i operator przypisania.

Ponadto szablon funkcji uniemożliwi zamianę obiektów różnych typów, ponieważ kompilator zna typy parametrów *a* i *b* w czasie kompilacji.

Mimo że funkcja ta może zostać wykonana przez funkcję nieszablonową, za pomocą wskaźników o typie void, wersja z szablonem jest bezpiecznego typu. Rozważ następujące wywołania:

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

Drugie wywołanie `MySwap` wyzwala błąd czasu kompilacji, ponieważ kompilator nie może wygenerować funkcji `MySwap` z parametrami różnego typu. Używając wskaźników typu void, oba wywołania funkcji spowodują poprawną kompilację, ale funkcja nie będzie działać poprawnie w czasie wykonywania.

Dopuszczalna jest jawna specyfikacja argumentów szablonu dla szablonu funkcji. Na przykład:

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

Gdy argument szablonu jest określony jawnie, wykonywane są zwykłe konwersje niejawne, aby przekonwertować argument funkcji na typ odpowiadający parametrom szablonu funkcji. W powyższym przykładzie kompilator wykona konwersję `j` do typu **char**.

## <a name="see-also"></a>Zobacz też

[Szablony](../cpp/templates-cpp.md)<br/>
[Tworzenie wystąpienia szablonu funkcji](../cpp/function-template-instantiation.md)<br/>
[Jawne tworzenie wystąpienia](../cpp/explicit-instantiation.md)<br/>
[Jawna specjalizacja szablonów funkcji](../cpp/explicit-specialization-of-function-templates.md)
