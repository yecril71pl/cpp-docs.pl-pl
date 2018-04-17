---
title: Atrybuty C++ Standard | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: d2dcce6b0e289588c426792a334ee4ec38d1ab5f
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="attributes-in-c"></a>Atrybuty w języku C++

C++ Standard definiuje zestaw atrybutów, a także umożliwia dostawcom kompilatora określają własne atrybuty (w przestrzeni nazw specyficznych dla dostawcy), ale kompilatory są wymagane do rozpoznania tylko te atrybuty, które są zdefiniowane w normie.

W niektórych przypadkach standardowe atrybuty pokrywają się z parametrami declspec specyficznych dla kompilatora. W programie Visual C++, można użyć `[[deprecated]]` zamiast za pomocą atrybutu `declspec(deprecated)` i atrybut zostanie rozpoznany przez kompilator żadnych zgodność. Dla wszystkich innych declspec parametrów, takich jak dllimport i dllexport nie ma jeszcze atrybutu odpowiednika, nadal należy użyć składni declspec. Atrybuty nie ma wpływu na system typów i nie zmienić znaczenie programu. Kompilatory zignorować wartości atrybutów, które nie uznają.

**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): W zakresie lista atrybutów, można określić przestrzeń nazw dla wszystkich nazw za pomocą jednej `using` introducer:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Atrybuty C++ Standard

W języku C ++ 11 atrybutów umożliwiają standardowych adnotacji konstrukcji języka C++ (w tym między innymi klasy, funkcje, zmienne i bloki) z dodatkowymi informacjami, który może lub nie może być specyficzny dla dostawcy. Kompilatora można użyć tych informacji do wygenerowania komunikaty informacyjne lub aby zastosował logikę specjalne, podczas kompilowania kodu oparte na atrybutach. Kompilator ignoruje wszystkie atrybuty, które nie rozpoznaje, co oznacza, że nie można definiować własnych niestandardowych atrybutów przy użyciu tej składni. Atrybuty są ujęte w nawiasy kwadratowe dwa razy:

```cpp
[[deprecated]]
void Foo(int);
```

Atrybuty reprezentują standardowych alternatywę do specyficznych dla dostawcy rozszerzeń, takich jak dyrektywy #pragma, __declspec() (Visual C++) lub &#95; &#95;atrybutu&#95; &#95; (GNU). Jednak nadal musisz użyć konstrukcji specyficznych dla dostawcy, w większości przypadków. Standardowe Określa aktualnie następujące atrybuty, które zgodnych kompilator powinien rozpoznać:

- `[[noreturn]]` Określa, że funkcja nigdy nie zwraca; innymi słowy zawsze zgłasza wyjątek. Kompilator można dostosować zasady jego kompilacja `[[noreturn]]` jednostek.

- `[[carries_dependency]]` Określa, że funkcja propaguje zależności danych kolejności względem synchronizacja wątku. Ten atrybut może odnosić się do co najmniej jeden parametr, aby określić, że argument przekazany w niesie zależności w treści funkcji. Ten atrybut może odnosić się do samej funkcji, aby określić, że wartość zwracana niesie zależności poza funkcji. Kompilator można użyć tych informacji do generowania kodu większą wydajność.

- `[[deprecated]]` **Visual Studio 2015 lub nowszy:** Określa, czy funkcja nie jest przeznaczony do użycia i może nie istnieć w przyszłych wersjach interfejsu biblioteki. Kompilator może być to komunikat informacyjny generowania kodu klienta próby wywołania funkcji. Można zastosować do deklaracji klasy, nazwa typu typedef, zmienną, elementu członkowskiego danych niestatycznych, funkcji, przestrzeni nazw, wyliczenie, moduł wyliczający lub specjalizacja szablonu.  

- `[[fallthrough]]` **Visual Studio 2017 lub nowszy:** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut może być używany w kontekście [przełącznika](switch-statement-cpp.md) instrukcje jako wskazówkę kompilator (lub wszystkich czytelników Kod) zamierzony zachowanie przepuszczająca. Kompilatora Visual C++ aktualnie nie ostrzega na zachowanie przepuszczająca, więc ten atrybut nie zachowanie kompilatora nie wpływu.

- `[[nodiscard]]` **Visual Studio 2017 wersji 15.3 i nowszych:** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że wartość zwracana przez funkcję nie jest przeznaczony do usunięcia. Generuje ostrzeżenie C4834, jak pokazano w poniższym przykładzie:

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 wersji 15.3 i nowszych:** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że zmienna, funkcji, klasy, — typedef, elementu członkowskiego danych niestatycznych, enum lub specjalizacja szablonu celowo nie może być używany. Kompilator nie Ostrzegaj, gdy jednostka oznaczona jako `[[maybe_unused]]` nie jest używany. Później można ponownie zadeklarować jednostki, która jest zadeklarowana bez atrybutu, przy użyciu atrybutu i na odwrót. Jednostka jest traktowany jako oznaczone po jego pierwszej deklaracji, który jest oznaczony jako są analizowane i pozostałej części tłumaczenia bieżącej jednostce tłumaczenia.

## <a name="microsoft-specific-attributes"></a>Atrybuty specyficzne dla firmy Microsoft

- `[[gsl::suppress(rules)]]` Ten atrybut specyficzne dla firmy Microsoft jest używany do pomijania ostrzeżeń z programy wymusić [wskazówki dotyczące pomocy technicznej biblioteki (GSL)](https://github.com/Microsoft/GSL) reguły w kodzie. Rozważmy na przykład następujący fragment kodu:

    ```cpp
    void main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

   Przykład wywołuje następujące ostrzeżenia:

   - 26494 (typ reguły 5: zawsze zainicjować obiektu.)

   - 26485 (3 zasada granic: nie tablicy na wskaźnik zniszczenie.)

   - 26481 (granice reguła 1: nie używaj arytmetyki wskaźnika. Użyj zakresu.)

   Pierwsze dwie ostrzeżenia wyzwalać podczas kompilowania tego kodu narzędzie analizy kodu CppCoreCheck zainstalowane i aktywowane. Ale trzecie ostrzeżenie nie wyzwalać z powodu atrybutu. Wszystkie profile granice można pominąć, pisząc [[gsl::suppress(bounds)]] bez uwzględniania określonej reguły. Wytyczne Core C++ są zaprojektowane ułatwia pisanie kodu lepsze i bezpieczniejsze. Atrybut Pomiń ułatwia wyłączyć ostrzeżenia, gdy nie chcieli.
