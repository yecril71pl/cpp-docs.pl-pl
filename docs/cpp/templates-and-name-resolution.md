---
title: Szablony i rozpoznawanie nazw
ms.date: 11/04/2016
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
ms.openlocfilehash: e4a53df0a192c1d7b7f376e4401eb99fcbf7d481
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611929"
---
# <a name="templates-and-name-resolution"></a>Szablony i rozpoznawanie nazw

W definicjach szablonów, istnieją trzy typy nazw.

- Nazwy zadeklarowane lokalnie, wraz z nazwą samego szablonu i wszelkimi nazwami zadeklarowanymi wewnątrz jego definicji.

- Nazwy z otaczającego zakresu poza definicją szablonu.

- Nazwy, które w jakiś sposób zależą od argumentów szablonu, nazywane nazwami zależnymi.

Mimo że dwie pierwsze nazwy dotyczą również zakresów klas i funkcji, to wymagane są specjalne reguły rozwiązywania nazw w definicjach szablonów, aby poradzić sobie ze złożonością dodaną przez nazwy zależne. Jest to spowodowane faktem, że kompilator wie o tych nazwach niewiele, dopóki nie zostanie utworzone wystąpienie szablonu, dlatego że nazwy mogą mieć zupełnie różne typy, w zależności od użytych argumentów szablonu. Nazwy niezależne są wyszukiwane zgodnie ze zwykłymi regułami oraz w punkcie definicji szablonu. Nazwy te, będące niezależnymi argumentami szablonu, są wyszukiwane raz dla wszystkich jego specjalizacji. Nazwy zależne nie są wyszukiwane, dopóki nie zostanie utworzone wystąpienie szablonu, a wyszukiwanie następuje osobno dla każdej specjalizacji.

Typ jest zależny, jeśli zależy od argumentów szablonu. W szczególności, typ jest zależny, jeśli jest:

- Argumentem szablonu:

    ```cpp
    T
    ```

- Nazwą kwalifikowaną z kwalifikacją zawierającą typ zależny:

    ```cpp
    T::myType
    ```

- Nazwą kwalifikowaną, jeśli część niekwalifikowana identyfikuje typ zależny:

    ```cpp
    N::T
    ```

- Typem „const” lub „volatile”, którego typ podstawowy jest typem zależnym:

    ```cpp
    const T
    ```

- Wskaźnikiem, odwołaniem, tablicą lub wskaźnikiem do funkcji opartym na typie zależnym:

    ```cpp
    T *, T &, T [10], T (*)()
    ```

- Tablicą, której rozmiar jest oparty na parametrze szablonu:

    ```cpp
    template <int arg> class X {
    int x[arg] ; // dependent type
    }
    ```

- Typem szablonowym utworzonym z parametru szablonu:

    ```cpp
    T<int>, MyTemplate<T>
    ```

## <a name="type-dependence-and-value-dependence"></a>Zależność typu i wartości

Nazwy i wyrażenia zależne od parametru szablonu są klasyfikowane jako zależne od typu lub zależne od wartości, w zależności od tego, czy parametr szablonu jest parametrem typu, czy parametrem wartości. Ponadto, żaden identyfikator zadeklarowany w szablonie jako zależny od typu argumentu szablonu, nie jest uważany jako zależny od wartości, tak jak typ całkowity lub wyliczeniowy zainicjowany wyrażeniem zależnym od wartości.

Wyrażenia zależne od typu i wartości są wyrażeniami, które zawierają zmienne zależne od typu lub wartości. Wyrażenia te mogą mieć różną semantykę, w zależności od użytych parametrów szablonu.

## <a name="see-also"></a>Zobacz także

[Szablony](../cpp/templates-cpp.md)