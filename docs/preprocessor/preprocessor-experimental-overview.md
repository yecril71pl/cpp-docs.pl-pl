---
title: MSVC eksperymentalnego preprocesora
description: Preprocesor MSVC jest aktualizowany pod kątem zgodności z językiem C/C++ standardami.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: eb861b18a8d42c73429f6d00a3f47b35c9b198ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090552"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC eksperymentalnego preprocesora

::: moniker range="vs-2015"

Program Visual Studio 2015 używa tradycyjnego preprocesora, który nie jest zgodny ze C++standardem. Eksperymentalny preprocesor jest dostępny w programie Visual Studio 2017 i Visual Studio 2019 przy użyciu przełącznika kompilatora [preprocesora/Experimental:](../build/reference/experimental-preprocessor.md) . Więcej informacji na temat korzystania z nowego preprocesora w programie Visual Studio 2017 i Visual Studio 2019 jest dostępne. Aby je wyświetlić, użyj selektora wersji dokumentacji, aby wybrać jedną z tych wersji.

::: moniker-end

::: moniker range=">=vs-2017"

Aktualizujemy preprocesor firmy C++ Microsoft w celu ulepszania zgodności ze standardami, naprawiania usterek od dawna dba i zmieniania niektórych zachowań, które są oficjalnie niezdefiniowane. Dodaliśmy również nową diagnostykę, aby ostrzec o błędach w definicjach makr.

Te zmiany są dostępne za pomocą przełącznika kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) w programie visual Studio 2017 lub visual Studio 2019. Domyślne zachowanie preprocesora pozostaje takie samo jak w poprzednich wersjach.

Począwszy od programu Visual Studio 2019 w wersji 16,5, Eksperymentalna obsługa preprocesora dla standardu C++ 20 jest kompletna.

## <a name="new-predefined-macro"></a>Nowe wstępnie zdefiniowane makro

Możesz wykryć, który preprocesor jest używany w czasie kompilacji. Sprawdź wartość wstępnie zdefiniowanego makra [\_MSVC\_tradycyjny](predefined-macros.md) , aby stwierdzić, czy tradycyjny preprocesor jest w użyciu. To makro jest ustawiane bezwarunkowo przez wersje kompilatora, które go obsługują, niezależnie od tego, który preprocesora jest wywoływany. Jej wartość jest równa 1 dla tradycyjnego preprocesora. Jest to 0 dla preprocesora.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Zmiany zachowania w eksperymentalnym preprocesorze

Początkowa prace nad eksperymentalnym preprocesorem koncentrują się na tym, że wszystkie rozwinięcia makra są zgodne ze standardem. Umożliwia używanie kompilatora MSVC z bibliotekami, które są aktualnie blokowane przez tradycyjne zachowania. Zaktualizowaliśmy preprocesor w rzeczywistych projektach świata. Poniżej przedstawiono niektóre z bardziej typowych zmian, które zostały znalezione:

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

Standardy-zgodność ze standardami polegają na zadeklaruje `int myVal` wewnątrz odpowiednich dyrektyw `#ifdef/#endif`:

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

W tym przypadku prefiks `L` jest niezbędny, ponieważ sąsiadujące literały ciągu są łączone po rozwinięciu tego makra. Poprawka zgodna z poprzednimi wersjami ma na celu zmianę definicji:

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

- Użyj łączenia ciągów `L""` i `#str` do dodawania prefiksu. Sąsiadujące literały ciągu są łączone po rozwinięciu makra:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Dodaj prefiks po `#str` jest ciągiem z dodatkowym rozwinięciem makra

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Aby połączyć tokeny, użyj operatora łączenia `##`. Kolejność operacji dla `##` i `#` jest nieokreślona, chociaż wszyscy kompilatory wydają ocenę operatora `#` przed `##` w tym przypadku.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Ostrzeżenie dotyczące nieprawidłowego \#\#

Gdy [operator wklejania tokenu (# #)](token-pasting-operator-hash-hash.md) nie powoduje pojedynczego prawidłowego tokenu przetwarzania wstępnego, zachowanie jest niezdefiniowane. Tradycyjny preprocesor w trybie dyskretnym nie może połączyć tokenów. Nowy preprocesor jest zgodny z zachowaniem większości innych kompilatorów i emituje diagnostykę.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Dla koprocedury przecinków w makrach wariadyczne

Tradycyjny preprocesor MSVC zawsze usuwa przecinki przed pustymi zamiennikami `__VA_ARGS__`. Eksperymentalny preprocesor bardziej blisko zachowuje zachowanie innych popularnych kompilatorów międzyplatformowych. Aby można było usunąć przecinek, argument wariadyczne musi być braku (nie tylko pusty) i musi być oznaczony operatorem `##`. Rozważmy następujący przykład:

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

W poniższym przykładzie w wywołaniu `FUNC2(1)` argumentu wariadyczne nie ma w wywoływanym makrze. W wywołaniu `FUNC2(1, )` argument wariadyczne jest pusty, ale nie ma go na liście argumentów.

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

W nadchodzącym standardzie C++ 20 ten problem został rozwiązany przez dodanie `__VA_OPT__`. Eksperymentalna obsługa preprocesora `__VA_OPT__` jest dostępna w programie Visual Studio 2019 w wersji 16,5.

### <a name="c20-variadic-macro-extension"></a>Rozszerzenie makra wariadyczne języka c++ 20

Eksperymentalny preprocesor obsługuje argument makra wariadyczne języka C++ 20 dla koprocedury:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Ten kod nie jest zgodny przed standardem C++ 20. W MSVC eksperymentalny preprocesor rozszerza to zachowanie języka C++ 20 do trybów standardowego języka ( **`/std:c++14`** , **`/std:c++17`** ). To rozszerzenie jest zgodne z zachowaniem innych głównych kompilatorów C++ międzyplatformowych.

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

Podczas rozszerzania `A()`tradycyjny preprocesor przekazuje wszystkie argumenty spakowane w `__VA_ARGS__` do pierwszego argumentu TWO_STRINGS, co pozostawia argument wariadyczne `TWO_STRINGS` puste. Powoduje to, że wynik `#first` będzie "1, 2" zamiast tylko "1". Jeśli masz ścisłą pracę, możesz zastanawiać się, co się stało z wynikami `#__VA_ARGS__` w tradycyjnym rozszerzeniu preprocesora: Jeśli parametr wariadyczne jest pusty, powinno być wynikiem pustego literału ciągu `""`. Oddzielny problem utrzymuje pusty token literału ciągu.

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

Mimo że ten przykład może wydawać się nieco contrived, został on wystawiony w kodzie świecie rzeczywistym. Aby zobaczyć, co się dzieje, można podzielić rozwinięcie, rozpoczynając od `DO_THING`:

1. `DO_THING(1, "World")` rozwiń do `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` rozszerza do `IMPL ## 1`, które rozszerzają się do `IMPL1`
1. Teraz tokeny są w tym stanie: `IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor wyszukuje identyfikator makra podobnej do funkcji `IMPL1`. Ponieważ nie następuje `(`, nie jest uważany za wywołanie makra podobnej do funkcji.
1. Preprocesor przechodzi do następujących tokenów. Znajduje makro podobne do funkcji, `ECHO` wywoływane: `ECHO(("Hello", "World"))`, które rozwija się do `("Hello", "World")`
1. `IMPL1` nigdy nie jest ponownie brana pod uwagę dla rozwinięcia, więc pełny wynik rozwinięcia to: `IMPL1("Hello", "World");`

Aby zmodyfikować makro tak samo jak w przypadku eksperymentalnego preprocesora i tradycyjnego preprocesora, Dodaj kolejną warstwę operatora:

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

Począwszy od programu Visual Studio 2019 w wersji 16,5, eksperymentalny preprocesor jest kompletny dla języka C++ 20. W poprzednich wersjach programu Visual Studio eksperymentalny preprocesor jest przede wszystkim kompletny, mimo że niektóre logika dyrektywy preprocesora nadal powraca do tradycyjnego zachowania. Oto częściowa lista niekompletnych funkcji w wersjach programu Visual Studio przed 16,5:

- Obsługa programu `_Pragma`
- Funkcje języka c++ 20
- Zwiększ usterkę blokującą: operatory logiczne w wyrażeniach stałych preprocesora nie są w pełni zaimplementowane w nowym preprocesorze przed wersją 16,5. W przypadku niektórych dyrektyw `#if` nowy preprocesor może wrócić do tradycyjnego preprocesora. Efekt jest zauważalny tylko wtedy, gdy makra niezgodne z tradycyjną preprocesorem zostaną rozwinięte. Może się tak zdarzyć podczas kompilowania miejsc preprocesora.

::: moniker-end
