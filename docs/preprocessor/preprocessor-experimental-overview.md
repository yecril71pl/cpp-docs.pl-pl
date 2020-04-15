---
title: Przegląd preprocesora eksperymentalnego MSVC
description: Preprocesor MSVC jest aktualizowany zgodnie ze standardami C/C++.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337480"
---
# <a name="msvc-experimental-preprocessor-overview"></a>Przegląd preprocesora eksperymentalnego MSVC

::: moniker range="vs-2015"

Visual Studio 2015 używa tradycyjnego preprocesora, który nie jest zgodny ze standardem C++. Eksperymentalny preprocesor jest dostępny w programie Visual Studio 2017 i programie Visual Studio 2019 przy użyciu przełącznika kompilatora [/experimental:preprocessor.](../build/reference/experimental-preprocessor.md) Więcej informacji na temat korzystania z nowego preprocesora w programie Visual Studio 2017 i programie Visual Studio 2019 jest dostępna. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2017"

Aktualizujemy preprocesor Microsoft C++, aby poprawić zgodność ze standardami, naprawić długotrwałe błędy i zmienić niektóre zachowania, które są oficjalnie niezdefiniowane. Dodaliśmy również nową diagnostykę, aby ostrzegać o błędach w definicjach makr.

Te zmiany są dostępne przy użyciu przełącznika kompilatora [/experimental:preprocesor](../build/reference/experimental-preprocessor.md) w programie Visual Studio 2017 lub Visual Studio 2019. Domyślne zachowanie preprocesora pozostaje takie samo jak w poprzednich wersjach.

Począwszy od programu Visual Studio 2019 w wersji 16.5, eksperymentalna obsługa preprocesora dla standardu C++20 jest pełna funkcji.

## <a name="new-predefined-macro"></a>Nowe wstępnie zdefiniowane makro

Można wykryć, który preprocesor jest używany w czasie kompilacji. Sprawdź wartość wstępnie zdefiniowanego makra [ \_\_MSVC TRADITIONAL,](predefined-macros.md) aby sprawdzić, czy używany jest tradycyjny preprocesor. To makro jest ustawiane bezwarunkowo przez wersje kompilatora, które go obsługują, niezależnie od którego wywoływany jest preprocesor. Jego wartość wynosi 1 dla tradycyjnego preprocesora. Jest to 0 dla zgodnego preprocesora.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Zmiany zachowania w preprocesorze eksperymentalnym

Początkowe prace nad eksperymentalnym preprocesorem koncentrowały się na tym, aby wszystkie rozszerzenia makr były zgodne ze standardem. Umożliwia użycie kompilatora MSVC z bibliotekami, które są obecnie blokowane przez tradycyjne zachowania. Przetestowaliśmy zaktualizowany preprocesor w rzeczywistych projektach. Oto niektóre z najczęstszych zmian, które znaleźliśmy:

### <a name="macro-comments"></a>Komentarze do makr

Tradycyjny preprocesor opiera się na buforach znaków, a nie tokenach preprocesora. Umożliwia nietypowe zachowanie, takie jak następująca sztuczka komentarza preprocesora, która nie działa w ramach zgodnego preprocesora:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Poprawka zgodna ze standardami `int myVal` polega na `#ifdef/#endif` deklarowaniu wewnątrz odpowiednich dyrektyw:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L#val

Tradycyjny preprocesor niepoprawnie łączy prefiks ciągu z wynikiem [operatora stringizing (#):](stringizing-operator-hash.md)

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

W takim przypadku `L` prefiks jest zbędne, ponieważ literały sąsiednich ciągów są łączone po rozwinieniu makra i tak. Poprawka zgodna z do tyłu polega na zmianie definicji:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Ten sam problem znajduje się również w makrach wygody, które "stringize" argument do szerokiego ciągu literal:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Problem można rozwiązać na różne sposoby:

- Użyj konkabitacji `L""` `#str` ciągu i dodać prefiks. Sąsiednie literały ciągów są łączone po rozwinieniu makra:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Dodaj prefiks `#str` po jest ciągniony z dodatkowym rozszerzeniem makra

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Operator łączenia służy `##` do łączenia tokenów. Kolejność operacji dla `##` `#` i jest nieokreślony, chociaż wszystkie kompilatory wydają się oceniać `#` operator wcześniej `##` w tym przypadku.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Ostrzeżenie o nieprawidłowym\#\#

Gdy [operator wklejania tokenu (##)](token-pasting-operator-hash-hash.md) nie powoduje pojedynczego prawidłowego tokenu przetwarzania wstępnego, zachowanie jest niezdefiniowane. Tradycyjny preprocesor po cichu nie łączy tokenów. Nowy preprocesor pasuje do zachowania większości innych kompilatorów i emituje diagnostykę.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Przecinek elision w makrach zmiennych

Tradycyjny preprocesor MSVC zawsze usuwa przecinki przed pustymi `__VA_ARGS__` zamiennikami. Eksperymentalny preprocesor bardziej śledzi zachowanie innych popularnych kompilatorów między platformami. Aby przecinek został usunięty, argument variadic musi brakować (nie tylko pusty) `##` i musi być oznaczony operatorem. Rozważmy następujący przykład:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

W poniższym przykładzie w `FUNC2(1)` wywołaniu argumentu variadic brakuje w wywoływanym makra. W wywołaniu `FUNC2(1, )` argumentu variadic jest pusty, ale nie brakuje (zwróć uwagę na przecinek na liście argumentów).

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

W nadchodzącym standardzie C++20 ten problem `__VA_OPT__`został rozwiązany przez dodanie . Eksperymentalna obsługa preprocesora `__VA_OPT__` jest dostępna od programu Visual Studio 2019 w wersji 16.5.

### <a name="c20-variadic-macro-extension"></a>Rozszerzenie makra variadic C++20

Eksperymentalny preprocesor obsługuje c++20 variadic makro argument elision:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Ten kod nie jest zgodny przed standardem C++20. W programie MSVC eksperymentalny preprocesor rozszerza to zachowanie języka C++20 na niższe tryby standardowe języka (**`/std:c++14`**, **`/std:c++17`**). To rozszerzenie pasuje do zachowania innych głównych kompilatorów C++ między platformami.

### <a name="macro-arguments-are-unpacked"></a>Argumenty makr są "rozpakowane"

W tradycyjnym preprocesorze, jeśli makro przekazuje jeden ze swoich argumentów do innego makro zależnego, argument nie zostanie "rozpakowany" po wstawieniu. Zazwyczaj ta optymalizacja pozostaje niezauważona, ale może prowadzić do nietypowego zachowania:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Podczas rozwijania, `A()`tradycyjny preprocesor przekazuje wszystkie argumenty `__VA_ARGS__` spakowane do pierwszego argumentu TWO_STRINGS, który pozostawia argument `TWO_STRINGS` variadic pusty. To powoduje, `#first` że wynik jest "1, 2", a nie tylko "1". Jeśli uważnie śledzisz, możesz się zastanawiać, co się stało `#__VA_ARGS__` z wynikiem tradycyjnego rozszerzenia preprocesora: jeśli parametr variadic jest pusty, powinien on spowodować pusty literał ciągu `""`. Oddzielny problem przechowywane pusty ciąg literał tokenu z generowane.

### <a name="rescanning-replacement-list-for-macros"></a>Ponowne skanowanie listy zastępów dla makr

Po wymianie makra tokeny wynikowe są ponownie skanowane w celu zastąpienia dodatkowych identyfikatorów makr. Algorytm używany przez tradycyjny preprocesor do wykonywania rescan nie jest zgodny, jak pokazano w tym przykładzie na podstawie rzeczywistego kodu:

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

Chociaż ten przykład może wydawać się nieco wymyślony, widzieliśmy go w rzeczywistym kodzie świata. Aby zobaczyć, co się dzieje, możemy rozbić `DO_THING`ekspansję, zaczynając od:

1. `DO_THING(1, "World")`rozszerza się na`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`rozszerza się `IMPL ## 1`do , który rozszerza się na`IMPL1`
1. Teraz tokeny są w tym stanie:`IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor odnajduje identyfikator `IMPL1`makra podobnego do funkcji . Ponieważ nie następuje `(`po nim , nie jest uważany za wywołanie makra podobnego do funkcji.
1. Preprocesor przechodzi do następujących tokenów. Znajduje się makro `ECHO` podobne do funkcji, które zostanie wywołane: `ECHO(("Hello", "World"))`, które rozszerza się do`("Hello", "World")`
1. `IMPL1`nigdy nie jest ponownie brana pod uwagę do ekspansji, więc pełny wynik ekspansji jest:`IMPL1("Hello", "World");`

Aby zmodyfikować makro tak samo w przypadku preprocesora doświadczalnego, jak i tradycyjnego preprocesora, dodaj kolejną warstwę pośrednictwu:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>Niekompletne funkcje

Począwszy od programu Visual Studio 2019 w wersji 16.5, eksperymentalny preprocesor jest kompletny dla języka C++20. W poprzednich wersjach programu Visual Studio eksperymentalny preprocesor jest w większości kompletny, chociaż niektóre logiki dyrektywy preprocesora nadal wraca do tradycyjnego zachowania. Oto częściowa lista niekompletnych funkcji w wersjach programu Visual Studio przed wersją 16.5:

- Wsparcie dla`_Pragma`
- Funkcje języka C++20
- Błąd blokowania doładowania: Operatory logiczne w wyrażeniach stałych preprocesora nie są w pełni zaimplementowane w nowym preprocesorze przed wersją 16.5. W `#if` niektórych dyrektywach nowy preprocesor może wrócić do tradycyjnego preprocesora. Efekt jest zauważalny tylko wtedy, gdy makra niezgodne z tradycyjnym preprocesorem zostają rozszerzone. Może się to zdarzyć podczas tworzenia slotów preprocesora Boost.

::: moniker-end
