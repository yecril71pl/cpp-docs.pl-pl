---
title: Wielokropek i szablony wariadyczne
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: e916dac40355f4397ef4846c0edf568c60b7d3dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221630"
---
# <a name="ellipsis-and-variadic-templates"></a>Wielokropek i szablony wariadyczne

W tym artykule pokazano, jak używać wielokropka ( `...` ) z szablonami języka C++ wariadyczne. Wielokropek ma wiele użycia w C i C++. Obejmują one listy zmiennych argumentów dla funkcji. `printf()`Funkcja z biblioteki środowiska uruchomieniowego języka C jest jednym z najbardziej znanych przykładów.

*Szablon wariadyczne* jest klasą lub szablonem funkcji, który obsługuje dowolną liczbę argumentów. Ten mechanizm jest szczególnie przydatny dla deweloperów biblioteki C++, ponieważ można go zastosować do szablonów klas i szablonów funkcji, a tym samym zapewnić szeroką gamę bezpiecznych i nieprostych funkcji oraz elastyczność.

## <a name="syntax"></a>Składnia

Wielokropek jest używany na dwa sposoby według szablonów wariadyczne. Po lewej stronie nazwy parametru oznacza *pakiet parametrów*, a po prawej stronie nazwy parametru rozszerza pakiety parametrów do oddzielnych nazw.

Oto przykład podstawowej składni definicji *klasy szablonu wariadyczne* :

```cpp
template<typename... Arguments> class classname;
```

W przypadku pakietów parametrów i rozszerzeń można dodać odstępy wokół wielokropka na podstawie preferencji, jak pokazano w poniższych przykładach:

```cpp
template<typename ...Arguments> class classname;
```

Lub:

```cpp
template<typename ... Arguments> class classname;
```

Zwróć uwagę, że w tym artykule jest stosowana Konwencja pokazana w pierwszym przykładzie (symbol wielokropka jest dołączony do **`typename`** ).

W powyższych przykładach *argumenty* są pakietem parametrów. Klasa `classname` może akceptować zmienną liczbę argumentów, jak w następujących przykładach:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Za pomocą definicji klasy szablonu wariadyczne można także wymagać co najmniej jednego parametru:

```cpp
template <typename First, typename... Rest> class classname;
```

Oto przykład podstawowej składni *funkcji szablonu wariadyczne* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Pakiet parametrów *argumentów* jest następnie rozwinięty do użycia, jak pokazano w następnej sekcji, **opisując szablony wariadyczne**.

Możliwe są inne formy składni funkcji szablonu wariadyczne — w tym następujące przykłady:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Specyfikatory takie jak **`const`** są również dozwolone:

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Podobnie jak w przypadku definicji klas szablonów wariadyczne, można utworzyć funkcje, które wymagają co najmniej jednego parametru:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Szablony wariadyczne używają `sizeof...()` operatora (niepowiązane ze starszym `sizeof()` operatorem):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Więcej informacji o rozmieszczeniu wielokropka

Wcześniej w tym artykule opisano rozmieszczenie wielokropka, które definiuje pakiety parametrów i rozszerzenia jako "po lewej stronie nazwy parametru, oznacza pakiet parametrów i po prawej stronie nazwy parametru rozszerza pakiety parametrów do oddzielnych nazw". Jest to technicznie prawdziwe, ale może być mylące w tłumaczeniu na kod. Rozważ następujące kwestie:

- Na liście parametrów szablonu ( `template <parameter-list>` ) `typename...` wprowadzono pakiet parametrów szablonu.

- W klauzuli deklaracji parametru ( `func(parameter-list)` ), wielokropek "najwyższego poziomu" wprowadza pakiet parametrów funkcji, a rozmieszczenie wielokropka jest ważne:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Gdy wielokropek pojawia się bezpośrednio po nazwie parametru, masz rozszerzenie pakietu parametrów.

## <a name="example"></a>Przykład

Dobrym sposobem zilustrowania mechanizmu funkcji szablonu wariadyczne jest użycie go w celu ponownego zapisu niektórych funkcji programu `printf` :

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Dane wyjściowe

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> Większość implementacji obejmujących funkcje szablonu wariadyczne korzysta z rekursji niektórych form, ale nieco różni się od tradycyjnej rekursji.  Tradycyjna rekursja obejmuje wywoływanie funkcji za pomocą tej samej sygnatury. (Może być przeciążony lub z szablonem, ale ten sam podpis jest wybierany za każdym razem). Rekursja wariadyczne obejmuje wywoływanie szablonu funkcji wariadyczne przy użyciu różnych (prawie zawsze malejących) liczb argumentów, a tym samym Wykreślanie innej sygnatury za każdym razem. Nadal wymagany jest "przypadek podstawowy", ale charakter rekursji jest inny.
