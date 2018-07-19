---
title: Atrybuty C++ Standard | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: 4a7ddcd7a83c64fe160d06d9b8ae378874e7518c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940680"
---
# <a name="attributes-in-c"></a>Atrybuty w języku C++

C++ Standard definiuje zestaw atrybutów, a także umożliwia dostawcom kompilatora zdefiniować własne atrybuty (w przestrzeni nazw specyficzne dla dostawcy), ale kompilatory są wymagane do rozpoznaje tylko te atrybuty, które są zdefiniowane w standardzie.

W niektórych przypadkach standardowe atrybuty pokrywają się z parametrami declspec specyficznych dla kompilatora. W programie Visual C++, można użyć `[[deprecated]]` atrybutu zamiast `declspec(deprecated)` i atrybut zostanie rozpoznane przez kompilator wszelkie zgodność. Wszystkie inne declspec parametrów, takich jak dllimport i dllexport nie ma jeszcze atrybut odpowiednika, należy nadal używać składni declspec. Atrybuty nie ma wpływu na system typów, a nie zmieniają znaczenie programu. Kompilatory ignorują wartości atrybutów, które ich nie rozpoznają.

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): W zakresie listę atrybutów, można określić przestrzeń nazw dla wszystkich nazw za pomocą jednego **przy użyciu** introducer:

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Atrybuty C++ Standard

W języku C ++ 11 atrybuty zapewnić standardowy sposób dodawać adnotacje do konstrukcji języka C++ (w tym między innymi klasy, funkcje, zmienne i bloków) z dodatkowymi informacjami, które mogą lub nie jest specyficzne dla dostawcy. Kompilator może dzięki tym informacjom można wygenerować komunikaty informacyjne lub aby zastosować logikę specjalną, podczas kompilowania kodu opartego na atrybutach. Kompilator ignoruje wszelkie atrybuty, które nie rozpoznaje, co oznacza, że nie można zdefiniować własne niestandardowe atrybuty przy użyciu tej składni. Atrybuty są ujęte w nawiasy kwadratowe podwójne:

```cpp
[[deprecated]]
void Foo(int);
```

Atrybuty reprezentują standardowych alternatywa specyficzne dla dostawcy rozszerzeń, takich jak dyrektywy #pragma, __declspec() (Visual C++) lub &#95; &#95;atrybut&#95; &#95; (GNU). Jednakże nadal należy użyć konstrukcji specyficzne dla dostawcy w większości przypadków. Standardowa obecnie określa następujące atrybuty rozpoznających odpowiadające kompilatora:

- `[[noreturn]]` Określa, że funkcja nigdy nie zwraca; innymi słowy go zawsze zgłasza wyjątek. Kompilator może dostosowywać jego zasady kompilacji `[[noreturn]]` jednostek.

- `[[carries_dependency]]` Określa, że funkcja propaguje zależności danych kolejność w odniesieniu do synchronizacji wątków. Atrybut można stosować do co najmniej jeden parametr, aby określić, że argument przekazany w niesie ze sobą zależności w treści funkcji. Ten atrybut można zastosować do samej funkcji, aby określić, że wartość zwracana niesie ze sobą zależności z funkcji. Kompilator można użyć tych informacji do generowania kodu bardziej wydajne.

- `[[deprecated]]` **Visual Studio 2015 i nowszych:** Określa, że funkcja nie ma ma być używany i może nie istnieć w przyszłych wersjach interfejsu biblioteki. Kompilator użyć tej funkcji do generowania komunikat informacyjny, gdy kod klienta podejmuje próbę wywołania funkcji. Można zastosować do deklaracji klasy, nazwę typedef, zmienną, element członkowski danych niestatyczna, funkcji, przestrzeni nazw, wyliczenia, moduł wyliczający lub specjalizacji szablonu.  

- `[[fallthrough]]` **Visual Studio 2017 i nowszym:** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut może być używany w kontekście [Przełącz](switch-statement-cpp.md) sprawozdań jako wskazówkę kompilator (lub kto czyta Kod:) przeznaczonej zachowanie fallthrough. Kompilator języka Visual C++ obecnie nie ostrzega owanie fallthrough, więc ten atrybut nie ma żadnych zachowanie kompilatora efekt.

- `[[nodiscard]]` **Visual Studio 2017 w wersji 15.3 lub nowszej:** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że wartość zwracaną przez funkcję nie jest przeznaczony do usunięcia. Generuje ostrzeżenia C4834, jak pokazano w poniższym przykładzie:

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]` **Visual Studio 2017 w wersji 15.3 lub nowszej:** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że zmiennej, funkcji, klasy, — typedef, element członkowski danych niestatyczna, enum lub specjalizacja szablonu celowo nie mogą być używane. Kompilator nie ostrzega, gdy jednostki oznaczone `[[maybe_unused]]` nie jest używany. Później można ponownie zadeklarować jednostki, która jest zadeklarowana bez atrybutu, za pomocą atrybutu i na odwrót. Jednostki jest traktowany jako oznaczony po jego pierwszej deklaracji, która jest oznaczona są analizowane, a w pozostałej części tłumaczenia w bieżącej jednostce tłumaczenia.

## <a name="microsoft-specific-attributes"></a>Atrybuty specyficzne dla firmy Microsoft

- `[[gsl::suppress(rules)]]` Ten atrybut specyficzne dla firmy Microsoft jest używany w sytuacji pominięcia ostrzeżenia z programy, które wymuszają [wytyczne dotyczące obsługi biblioteki (GSL)](https://github.com/Microsoft/GSL) reguł w kodzie. Na przykład rozważmy następujący fragment kodu:

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

   Przykład wywołuje te ostrzeżenia:

   - 26494 (typ reguły 5: zawsze Inicjuj obiekt.)

   - 26485 (granice zasady 3: nie zanikania tablicy do wskaźnika.)

   - 26481 (granice reguła 1: nie używaj arytmetyki wskaźnika. Użyj zakresu.)

   Pierwsze dwa ostrzeżenia uruchamiał się po skompilować ten kod za pomocą narzędzia analizy kodu CppCoreCheck zainstalowane i aktywowane. Ale trzecie ostrzeżenie nie zostanie wyzwolony, ze względu na ten atrybut. Cały profil granic można pominąć, pisząc [[gsl::suppress(bounds)]] bez uwzględniania numer określonej reguły. Podstawowych wytycznych dotyczących języka C++ mają na celu pomóc w pisaniu lepiej i bezpieczniejszego kodu. Ten atrybut Pomiń ułatwia wyłączyć ostrzeżenia, gdy nie chcieli.
