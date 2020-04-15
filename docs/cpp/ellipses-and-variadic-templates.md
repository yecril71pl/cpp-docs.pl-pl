---
title: Wielokropki i szablony wariadyczne
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 358cdeeaf6f3e8c7f7841bbc796eca6557ccd145
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366336"
---
# <a name="ellipses-and-variadic-templates"></a>Wielokropki i szablony wariadyczne

W tym artykule pokazano, jak`...`używać wielokropek ( ) z szablonami variadic języka C++. Wielokropek miał wiele zastosowań w C i C ++. Obejmują one listy argumentów zmiennych dla funkcji. Funkcja `printf()` z biblioteki wykonawczej C jest jednym z najbardziej znanych przykładów.

Szablon *variadic* to szablon klasy lub funkcji, który obsługuje dowolną liczbę argumentów. Ten mechanizm jest szczególnie przydatne dla deweloperów biblioteki Języka C++, ponieważ można go zastosować do szablonów klas i szablonów funkcji, a tym samym zapewnić szeroki zakres funkcji typu bezpieczne i nietrywialne i elastyczność.

## <a name="syntax"></a>Składnia

Wielokropek jest używany na dwa sposoby przez szablony variadic. Po lewej stronie nazwy parametru oznacza *pakiet parametrów,* a po prawej stronie nazwy parametru rozszerza pakiety parametrów na oddzielne nazwy.

Oto podstawowy przykład składni definicji *klasy szablonu variadic:*

```cpp
template<typename... Arguments> class classname;
```

W przypadku pakietów parametrów i rozszerzeń można dodać odstępy wokół wielokropek, w zależności od preferencji, jak pokazano w poniższych przykładach:

```cpp
template<typename ...Arguments> class classname;
```

Lub to:

```cpp
template<typename ... Arguments> class classname;
```

Należy zauważyć, że w tym artykule używa konwencji, która jest wyświetlana `typename`w pierwszym przykładzie (wielokropek jest dołączony do ).

W poprzednich przykładach *Argumenty* jest pakiet parametrów. Klasa `classname` może akceptować zmienną liczbę argumentów, jak w tych przykładach:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Za pomocą variadic definicji klasy szablonu, można również wymagać co najmniej jeden parametr:

```cpp
template <typename First, typename... Rest> class classname;
```

Oto podstawowy przykład składni *funkcji szablonu variadic:*

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Pakiet *parametrów Argumenty* jest następnie rozwijany do użytku, jak pokazano w następnej sekcji **Opis szablonów zmiennowiskowych**.

Możliwe są inne formy składni funkcji szablonu variadic — w tym między innymi następujące przykłady:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Specyfikatory, takie jak **const** są również dozwolone:

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Podobnie jak w definicji klas szablonów variadic, można tworzyć funkcje, które wymagają co najmniej jednego parametru:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Szablony variadic `sizeof...()` używają operatora (niezwiązanego ze starszym `sizeof()` operatorem):

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

Wcześniej w tym artykule opisano położenie wielokropka, który definiuje pakiety parametrów i rozszerzenia jako "po lewej stronie nazwy parametru, oznacza pakiet parametrów, a po prawej stronie nazwy parametru rozszerza pakiety parametrów na oddzielne nazwy". Jest to technicznie prawda, ale może być mylące w tłumaczeniu na kod. Rozważ następujące kwestie:

- Na liście parametrów szablonu (`template <parameter-list>`) `typename...` wprowadza pakiet parametrów szablonu.

- W klauzuli deklaracji parametrów (`func(parameter-list)`) wielokropek "najwyższego poziomu" wprowadza pakiet parametrów funkcyjnych, a pozycjonowanie wielokropka jest ważne:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- W przypadku, gdy wielokropek pojawia się natychmiast po nazwie parametru, masz rozszerzenie pakietu parametrów.

## <a name="example"></a>Przykład

Dobrym sposobem zilustrowania mechanizmu funkcji szablonu zmiennego jest użycie go w ponownym zapisie niektórych `printf`funkcji:

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
> Większość implementacji, które zawierają funkcje szablonu variadic używać rekursji jakiejś formy, ale nieznacznie różni się od tradycyjnej rekursji.  Tradycyjna rekursja obejmuje funkcję wywołującą się przy użyciu tego samego podpisu. (Może być przeciążony lub szablon, ale ten sam podpis jest wybierany za każdym razem.) Rekursja variadic polega na wywoływaniu szablonu funkcji zmiennej przy użyciu różnej (prawie zawsze zmniejszającej się) liczby argumentów, a tym samym wykreślaniu innego podpisu za każdym razem. "Przypadek bazowy" jest nadal wymagany, ale charakter rekursji jest inny.
