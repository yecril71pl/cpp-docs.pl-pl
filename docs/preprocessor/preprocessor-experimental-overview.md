---
title: Przegląd MSVC nowego preprocesora
description: Preprocesor MSVC jest aktualizowany pod kątem zgodności ze standardami C/C++.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor, experimental
- preprocessor, new
ms.openlocfilehash: c95f923d8c38250958e26431b61a71a1e6a7fdda
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041370"
---
# <a name="msvc-new-preprocessor-overview"></a>Przegląd MSVC nowego preprocesora

::: moniker range="vs-2015"

Program Visual Studio 2015 używa tradycyjnego preprocesora, który nie jest zgodny ze standardem C++ lub C99. Począwszy od programu Visual Studio 2019 w wersji 16,5, Nowa obsługa preprocesora dla standardu C++ 20 jest kompletna. Te zmiany są dostępne za pomocą przełącznika kompilatora [/Zc: preprocesora](../build/reference/zc-preprocessor.md) . Wersja eksperymentalna nowego preprocesora jest dostępna w programie Visual Studio 2017 w wersji 15,8 lub nowszej przy użyciu przełącznika kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) . Więcej informacji na temat korzystania z nowego preprocesora w programie Visual Studio 2017 i Visual Studio 2019 jest dostępne. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj kontrolki selektora **wersji** . Znajduje się w górnej części spisu treści na tej stronie.

::: moniker-end

::: moniker range=">=vs-2017"

Aktualizujemy preprocesor Microsoft C++, aby poprawić zgodność ze standardami, rozwiązać od dawna dba błędów i zmienić niektóre zachowania, które są oficjalnie niezdefiniowane. Dodaliśmy również nową diagnostykę, aby ostrzec o błędach w definicjach makr.

Począwszy od programu Visual Studio 2019 w wersji 16,5, preprocesora w standardzie C++ 20 jest funkcja kompletna. Te zmiany są dostępne za pomocą przełącznika kompilatora [/Zc: preprocesora](../build/reference/zc-preprocessor.md) . Wersja eksperymentalna nowego preprocesora jest dostępna we wcześniejszych wersjach, począwszy od programu Visual Studio 2017 w wersji 15,8. Można ją włączyć za pomocą przełącznika kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) . Domyślne zachowanie preprocesora pozostaje takie samo jak w poprzednich wersjach.

## <a name="new-predefined-macro"></a>Nowe wstępnie zdefiniowane makro

Możesz wykryć, który preprocesor jest używany w czasie kompilacji. Sprawdź wartość wstępnie zdefiniowanego makra, [`_MSVC_TRADITIONAL`](predefined-macros.md) Aby stwierdzić, czy tradycyjny preprocesor jest w użyciu. To makro jest ustawiane bezwarunkowo przez wersje kompilatora, które go obsługują, niezależnie od tego, który preprocesora jest wywoływany. Jej wartość jest równa 1 dla tradycyjnego preprocesora. Jest to 0 dla preprocesora.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-new-preprocessor"></a>Zmiany zachowania w nowym preprocesorze

Początkowa pracy nad nowym preprocesorem koncentruje się na tym, że wszystkie rozwinięcia makra są zgodne ze standardem. Umożliwia używanie kompilatora MSVC z bibliotekami, które są aktualnie blokowane przez tradycyjne zachowania. Zaktualizowaliśmy preprocesor w rzeczywistych projektach świata. Poniżej przedstawiono niektóre z bardziej typowych zmian, które zostały znalezione:

### <a name="macro-comments"></a>Komentarze makr

Tradycyjny preprocesor jest oparty na buforach znaków zamiast tokenów preprocesora. Pozwala to na nietypowe zachowanie, takie jak następująca lewa do komentarza preprocesora, która nie działa w ramach preprocesora:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Standardy — zgodność ze standardami polega na zadeklaruje `int myVal` wewnątrz odpowiednich `#ifdef/#endif` dyrektyw:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # Val

Tradycyjny preprocesor niepoprawnie łączy prefiks ciągu z wynikiem operatora [tworzenia ciągu (#)](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

W tym przypadku `L` prefiks jest niezbędny, ponieważ sąsiadujące literały ciągu są łączone po rozwinięciu tego makra. Poprawka zgodna z poprzednimi wersjami ma na celu zmianę definicji:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Ten sam problem znajduje się również w wygodnych makrach, które "łańcuchujący" argumentem do szerokiego literału ciągu:

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Problem można rozwiązać na różne sposoby:

- Użyj łączenia ciągów `L""` i, `#str` Aby dodać prefiks. Sąsiadujące literały ciągu są łączone po rozwinięciu makra:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Dodaj prefiks po `#str` ciągu z dodatkowym rozwinięciem makra

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Użyj operatora łączenia, `##` Aby połączyć tokeny. Kolejność operacji dla `##` i `#` jest nieokreślona, mimo że wszystkie kompilatory pozornie `#` `##` wystawią operator w tym przypadku.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Ostrzeżenie dla nieprawidłowego \#\#

Gdy [operator wklejania tokenu (# #)](token-pasting-operator-hash-hash.md) nie powoduje pojedynczego prawidłowego tokenu przetwarzania wstępnego, zachowanie jest niezdefiniowane. Tradycyjny preprocesor w trybie dyskretnym nie może połączyć tokenów. Nowy preprocesor jest zgodny z zachowaniem większości innych kompilatorów i emituje diagnostykę.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Dla koprocedury przecinków w makrach wariadyczne

Tradycyjny preprocesor MSVC zawsze usuwa przecinki przed pustymi `__VA_ARGS__` zamiennikami. Nowy preprocesor jest bardziej blisko zachowaniem innych popularnych kompilatorów międzyplatformowych. Aby można było usunąć przecinek, argument wariadyczne musi być braku (nie tylko pusty) i musi być oznaczony `##` operatorem. Rozpatrzmy następujący przykład:

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

W poniższym przykładzie w wywołaniu wywołania `FUNC2(1)` argumentu wariadyczne brakuje makra. W wywołaniu `FUNC2(1, )` argumentu wariadyczne jest puste, ale nie ma go na liście argumentów.

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

W nadchodzącym standardzie języka C++ 20 ten problem został rozwiązany przez dodanie `__VA_OPT__` . Nowa obsługa preprocesora dla programu  `__VA_OPT__` jest dostępna w programie Visual Studio 2019 w wersji 16,5.

### <a name="c20-variadic-macro-extension"></a>Rozszerzenie makra wariadyczne języka c++ 20

Nowy preprocesor obsługuje argument makra wariadyczne języka C++ 20 dla koprocedury:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Ten kod nie jest zgodny przed standardem C++ 20. W programie MSVC nowy preprocesor rozszerza to zachowanie języka C++ 20 do trybu standardowego języka ( **`/std:c++14`** , **`/std:c++17`** ). To rozszerzenie jest zgodne z zachowaniem innych głównych kompilatorów języka C++ dla wielu platform.

### <a name="macro-arguments-are-unpacked"></a>Argumenty makr są "rozpakowane"

W tradycyjnych preprocesorach, jeśli makro przekazuje jeden z argumentów do innego zależne makro, argument nie zostanie "rozpakowany", gdy zostanie wstawiony. Zwykle Ta optymalizacja nie jest zauważalna, ale może prowadzić do nietypowego zachowania:

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

Podczas rozszerzania `A()` tradycyjny preprocesor przekazuje wszystkie argumenty spakowane w `__VA_ARGS__` do pierwszego argumentu TWO_STRINGS, co pozostawia argument wariadyczne `TWO_STRINGS` pustego. Powoduje to, że wynikiem `#first` będzie "1, 2", a nie tylko "1". Jeśli masz ścisłą pracę, możesz zastanawiać się, co się stało z wynikami `#__VA_ARGS__` w tradycyjnym rozszerzeniu preprocesora: Jeśli parametr wariadyczne jest pusty, powinien wynikać z pustym literałem ciągu `""` . Oddzielny problem utrzymuje pusty token literału ciągu.

### <a name="rescanning-replacement-list-for-macros"></a>Ponowne skanowanie listy zastępczej dla makr

Po wymianie makra powstające tokeny są ponownie skanowane pod kątem dodatkowych identyfikatorów makr, które mają zostać zastąpione. Algorytm używany przez tradycyjny preprocesor w celu przeprowadzenia ponownego skanowania nie jest zgodny, jak pokazano w tym przykładzie na podstawie rzeczywistego kodu:

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

Chociaż ten przykład może wydawać się bitowym contrived, jest on widoczny w rzeczywistym kodzie.

Aby zobaczyć, co się dzieje, możemy rozdzielić rozwinięcie, rozpoczynając od `DO_THING` :

1. `DO_THING(1, "World")` rozwija się do `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` rozwija do `IMPL ## 1` , który rozwija się do `IMPL1`
1. Teraz tokeny są w tym stanie: `IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor wyszukuje identyfikator makra podobnej do funkcji `IMPL1` . Ponieważ nie następuje, nie jest `(` uważany za wywołanie makra podobnej do funkcji.
1. Preprocesor przechodzi do następujących tokenów. Odnajdzie makro podobne do funkcji `ECHO` wywoływane: `ECHO(("Hello", "World"))` , które rozwija się do `("Hello", "World")`
1. `IMPL1` nigdy nie jest ponownie brany pod uwagę dla rozwinięcia, więc pełny wynik rozwinięcia to: `IMPL1("Hello", "World");`

Aby zmodyfikować makro tak samo jak w przypadku nowego preprocesora i tradycyjnego preprocesora, Dodaj kolejną warstwę operatora:

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

## <a name="incomplete-features-before-165"></a>Niekompletne funkcje przed 16,5

Począwszy od programu Visual Studio 2019 w wersji 16,5, nowy preprocesor to funkcja kompletna dla języka C++ 20. W poprzednich wersjach programu Visual Studio nowy preprocesor jest przeważnie kompletny, mimo że niektóre logika dyrektywy preprocesora nadal powraca do tradycyjnego zachowania. Oto częściowa lista niekompletnych funkcji w wersjach programu Visual Studio przed 16,5:

- Obsługa `_Pragma`
- Funkcje języka c++ 20
- Zwiększ usterkę blokującą: operatory logiczne w wyrażeniach stałych preprocesora nie są w pełni zaimplementowane w nowym preprocesorze przed wersją 16,5. W przypadku niektórych `#if` dyrektyw nowy preprocesor może wrócić do tradycyjnego preprocesora. Efekt jest zauważalny tylko wtedy, gdy makra niezgodne z tradycyjną preprocesorem zostaną rozwinięte. Może się tak zdarzyć podczas kompilowania miejsc preprocesora.

::: moniker-end
