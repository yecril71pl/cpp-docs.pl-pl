---
title: Szablony funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: 77f3d1ee704c8094fd3bd94597311976e54ba6a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493525"
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

Ten kod definiuje rodzinę funkcji, które zamieniają wartości argumentów. Za pomocą tego szablonu możesz wygenerować funkcje, które będą zamieniać **int** i **długie** typów, a także typy zdefiniowane przez użytkownika. `MySwap` będzie zamieniać nawet klasy, jeśli w klasie został poprawnie zdefiniowany konstruktor kopiujący i operator przypisania.

Ponadto, szablon funkcji zapobiega zamienianiu obiektów różnych typów, ponieważ kompilator zna typy *a* i *b* parametrów w czasie kompilacji.

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

Gdy argument szablonu jest określony jawnie, wykonywane są zwykłe konwersje niejawne, aby przekonwertować argument funkcji na typ odpowiadający parametrom szablonu funkcji. W powyższym przykładzie, kompilator konwertuje `char j` na typ **int**.

## <a name="see-also"></a>Zobacz także

[Szablony](../cpp/templates-cpp.md)<br/>
[Tworzenie wystąpienia szablonu funkcji](../cpp/function-template-instantiation.md)<br/>
[Jawne tworzenie wystąpienia](../cpp/explicit-instantiation.md)<br/>
[Jawna specjalizacja szablonów funkcji](../cpp/explicit-specialization-of-function-templates.md)