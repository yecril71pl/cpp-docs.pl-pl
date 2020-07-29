---
title: Atrybuty w języku C++
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: efdc62e2343135aee483520f633bac99519455b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229210"
---
# <a name="attributes-in-c"></a>Atrybuty w języku C++

Standard C++ definiuje zestaw atrybutów, a także umożliwia dostawcom kompilatora Definiowanie własnych atrybutów (w ramach przestrzeni nazw specyficznych dla dostawcy), ale kompilatory są wymagane do rozpoznawania tylko atrybutów zdefiniowanych w standardzie.

W niektórych przypadkach standardowe atrybuty nakładają się na specyficzne dla kompilatora parametry declspec. W Visual C++, można użyć `[[deprecated]]` atrybutu zamiast przy użyciu, `declspec(deprecated)` a atrybut zostanie rozpoznany przez dowolny kompilator zgodny. Dla wszystkich innych parametrów declspec, takich jak dllimport i dllexport, nie istnieje jeszcze odpowiednik atrybutu, dlatego należy nadal używać składni declspec. Atrybuty nie wpływają na system typów i nie zmieniają znaczenia programu. Kompilatory ignorują wartości atrybutów, które nie są rozpoznawane.

**Visual Studio 2017 w wersji 15,3 i nowszej** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): w zakresie listy atrybutów można określić przestrzeń nazw dla wszystkich nazw za pomocą pojedynczego dopełnienia **`using`** :

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>Standardowe atrybuty języka C++

W języku C++ 11 atrybuty udostępniają ustandaryzowany sposób dodawania adnotacji do konstrukcji języka C++ (w tym między innymi klasy, funkcje, zmienne i bloki) z dodatkowymi informacjami, które mogą lub nie mogą być specyficzne dla dostawcy. Kompilator może używać tych informacji do generowania komunikatów informacyjnych lub do stosowania logiki specjalnej podczas kompilowania kodu z atrybutami. Kompilator ignoruje wszystkie atrybuty, które nie są rozpoznawane, co oznacza, że nie można definiować własnych atrybutów niestandardowych przy użyciu tej składni. Atrybuty są ujęte w podwójne nawiasy kwadratowe:

```cpp
[[deprecated]]
void Foo(int);
```

Atrybuty reprezentują standardowe alternatywy dla rozszerzeń specyficznych dla dostawcy, takich jak dyrektywy #pragma, __declspec () (Visual C++) lub &#95;&#95;atrybutu&#95;&#95;  (GNU). Jednak w większości przypadków nadal trzeba będzie używać konstrukcji specyficznych dla dostawcy. Standard obecnie określa następujące atrybuty, które powinny być rozpoznawane przez kompilator zgodny:

- `[[noreturn]]`Określa, że funkcja nigdy nie zwraca; Innymi słowy, zawsze zgłasza wyjątek. Kompilator może dostosować reguły kompilacji dla `[[noreturn]]` jednostek.

- `[[carries_dependency]]`Określa, że funkcja propaguje kolejność zależności danych w odniesieniu do synchronizacji wątków. Ten atrybut może być stosowany do jednego lub kilku parametrów, aby określić, że argument, który przekazuje zależność do treści funkcji. Ten atrybut może być stosowany do samej funkcji, aby określić, że wartość zwracana wykonuje zależność od funkcji. Kompilator może używać tych informacji do generowania bardziej wydajnego kodu.

- `[[deprecated]]`**Program Visual Studio 2015 lub nowszy:** Określa, że funkcja nie jest przeznaczona do użycia i może nie istnieć w przyszłych wersjach interfejsu biblioteki. Kompilator może użyć tego do wygenerowania komunikatu informacyjnego, gdy kod klienta próbuje wywołać funkcję. Można zastosować do deklaracji klasy, typedef-Name, Variable, niestatycznej składowej danych, funkcji, przestrzeni nazw, wyliczenia, modułu wyliczającego lub specjalizacji szablonu.

- `[[fallthrough]]`**Visual Studio 2017 i nowsze:** (dostępne w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atrybut może być używany w kontekście instrukcji [Switch](switch-statement-cpp.md) jako wskazówkę do kompilatora (lub każda osoba odczytująca kod), że zachowanie fallthrough jest zamierzone. Kompilator języka Microsoft C++ obecnie nie ostrzega o zachowania fallthrough, więc ten atrybut nie ma wpływu na działanie kompilatora.

- `[[nodiscard]]`**Program Visual Studio 2017 w wersji 15,3 i nowszej:** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że wartość zwracana przez funkcję nie jest przeznaczona do odrzucania. Podnosi C4834 ostrzegawczy, jak pokazano w tym przykładzie:

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Program Visual Studio 2017 w wersji 15,3 i nowszej:** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) określa, że nie można użyć zmiennej, funkcji, klasy, typedef, niestatycznej składowej danych, wyliczenia lub specjalizacji szablonu. Kompilator nie ostrzega, gdy jednostka oznaczona `[[maybe_unused]]` nie jest używana. Jednostka zadeklarowana bez atrybutu może być później ponownie zadeklarowana z atrybutem i na odwrót. Jednostka jest traktowana jako oznaczona po pierwszej deklaracji oznaczonej jako przeanalizowanej, a w przypadku pozostałej translacji bieżącej jednostki tłumaczenia.

## <a name="microsoft-specific-attributes"></a>Atrybuty specyficzne dla firmy Microsoft

- `[[gsl::suppress(rules)]]`Ten atrybut specyficzny dla firmy Microsoft służy do pomijania ostrzeżeń od sprawdzających, które wymuszają reguły [biblioteki obsługi (GSL)](https://github.com/Microsoft/GSL) w kodzie. Na przykład rozważmy następujący fragment kodu:

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  Przykład wywołuje następujące ostrzeżenia:

  - 26494 (reguła typu 5: zawsze Inicjuj obiekt).

  - 26485 (reguła związana z regułą 3): brak tablicy do wskaźnika.

  - 26481 (reguła dotycząca granic 1: nie używaj arytmetyki wskaźnika. Użyj zamiast tego zakresu.)

  Pierwsze dwa ostrzeżenia są wyzwalane podczas kompilowania tego kodu z zainstalowanym i aktywowanym narzędziem CppCoreCheck Code Analysis. Ale trzecie ostrzeżenie nie jest wyzwalane z powodu atrybutu. Możesz pominąć profil całego ograniczenia, pisząc [[GSL:: pomijanie (Bounds)]] bez dołączania określonego numeru reguły. Podstawowe wytyczne dotyczące języka C++ zaprojektowano w celu ułatwienia pisania lepszego i bezpieczniejszego kodu. Atrybut pomijania ułatwia wyłączenie ostrzeżeń, gdy nie są one potrzebne.
  