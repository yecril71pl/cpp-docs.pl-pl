---
title: MSVC eksperymentalnego preprocesora
description: Preprocesor MSVC jest aktualizowany pod kątem zgodności z językiem C/C++ standardami.
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797177"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC eksperymentalnego preprocesora

Preprocesor C++ firmy Microsoft jest obecnie aktualizowany w celu poprawy zgodności ze standardami, naprawiania usterek od dawna dba i zmieniania niektórych zachowań, które są oficjalnie niezdefiniowane. Ponadto dodano nową diagnostykę, aby ostrzec o błędach w definicjach makr.

Te zmiany w bieżącym stanie są dostępne za pomocą przełącznika kompilatora [/Experimental: preprocesora](../build/reference/experimental-preprocessor.md) w programie visual Studio 2017 lub visual Studio 2019. Domyślne zachowanie preprocesora pozostaje takie samo jak w poprzednich wersjach.

## <a name="new-predefined-macro"></a>Nowe wstępnie zdefiniowane makro

Możesz wykryć, który preprocesor jest używany w czasie kompilacji. Sprawdź wartość wstępnie zdefiniowanego makra [\_MSVC\_tradycyjny](predefined-macros.md) , aby stwierdzić, czy tradycyjny preprocesor jest w użyciu. To makro jest ustawiane bezwarunkowo przez wersje kompilatora, które go obsługują, niezależnie od tego, który preprocesora jest wywoływany. Jej wartość jest równa 1 dla tradycyjnego preprocesora. Jest to 0 w przypadku zgodnego preprocesora doświadczalnego:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Zmiany zachowania w eksperymentalnym preprocesorze

Początkowa prace nad eksperymentalnym preprocesorem koncentrują się na wprowadzaniu wszystkich rozwinięcia makra w celu umożliwienia używania kompilatora MSVC z bibliotekami, które są obecnie blokowane z powodu tradycyjnych zachowań. Poniżej znajduje się lista niektórych najbardziej typowych zmian, które zostały uruchomione podczas testowania zaktualizowanego preprocesora z rzeczywistymi projektami świata.

### <a name="macro-comments"></a>Komentarze makr

Tradycyjny preprocesor jest oparty na buforach znaków zamiast tokenów preprocesora. Pozwala to na nietypowe zachowanie, takie jak następująca funkcja komentarza preprocesora, która nie będzie działała w ramach preprocesora:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Zgodne ze standardami poprawki są deklarowane `int myVal` wewnątrz odpowiednich dyrektyw `#ifdef/#endif`:

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

W takim przypadku prefiks `L` jest zbędny, ponieważ sąsiadujące literały ciągu są łączone po rozwinięciu tego makra. Poprawka zgodna z poprzednimi wersjami ma na celu zmianę definicji na następującą:

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

- Użyj łączenia ciągów `L""` i `#str` do dodawania prefiksu. To działa, ponieważ sąsiadujące literały ciągu są łączone po rozwinięciu makra:

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

Gdy [operator wklejania tokenu (# #)](token-pasting-operator-hash-hash.md) nie powoduje pojedynczego prawidłowego tokenu przetwarzania wstępnego, zachowanie jest niezdefiniowane. Tradycyjny preprocesor w trybie dyskretnym nie będzie mógł połączyć tokenów. Nowy preprocesor będzie zgodny z zachowaniem większości innych kompilatorów i emituje diagnostykę.

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
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

W poniższym przykładzie w wywołaniu `FUNC2(1)` argumentu wariadyczne brakuje w makrze evoked. W wywołaniu `FUNC2(1, )` argument wariadyczne jest pusty, ale nie ma go na liście argumentów.

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

W nadchodzącym standardzie C + + 2a ten problem został rozwiązany przez dodanie `__VA_OPT__`, która nie została jeszcze zaimplementowana.

### <a name="macro-arguments-are-unpacked"></a>Argumenty makr są "rozpakowane"

W tradycyjnych preprocesorach, jeśli makro przekazuje jeden z argumentów do innego zależnego makro, argument nie zostanie "rozpakowany", gdy zostanie zastąpiony. Zwykle Ta optymalizacja nie jest zauważalna, ale może prowadzić do nietypowego zachowania:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conformant preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Podczas rozszerzania `A()`tradycyjny preprocesor przekazuje wszystkie argumenty spakowane w `__VA_ARGS__` do pierwszego argumentu TWO_STRINGS, co pozostawia argument wariadyczne `TWO_STRINGS` pusty. Powoduje to, że wynik `#first` będzie "1, 2" zamiast tylko "1". Jeśli masz ścisłą pracę, możesz zastanawiać się, co się stało z wynikami `#__VA_ARGS__` w tradycyjnym rozszerzeniu preprocesora: Jeśli parametr wariadyczne jest pusty, powinno być wynikiem pustego literału ciągu `""`. Z powodu oddzielnego problemu nie Wygenerowano tokenu pustego literału ciągu.

### <a name="rescanning-replacement-list-for-macros"></a>Ponowne skanowanie listy zastępczej dla makr

Po wymianie makra, obliczone tokeny są ponownie skanowane pod kątem dodatkowych identyfikatorów makr, które muszą zostać zastąpione. Algorytm używany przez tradycyjny preprocesor w celu przeprowadzenia ponownego skanowania nie jest zgodny, jak pokazano w tym przykładzie na podstawie rzeczywistego kodu:

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
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

Mimo że ten przykład wygląda na bitowy contrived, okazało się, że występuje kod w świecie rzeczywistym. Aby zobaczyć, co się dzieje, możemy rozdzielić rozwinięcie, rozpoczynając od `DO_THING`:

1. `DO_THING(1, "World")` rozwiń do `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` rozszerza do `IMPL ## 1`, które rozszerzają się do `IMPL1`
1. Teraz tokeny są w tym stanie: `IMPL1 ECHO(("Hello", "World"))`
1. Preprocesor wyszukuje identyfikator makra przypominający funkcję `IMPL1`, ale nie następuje `(`, dlatego nie jest uważany za wywołanie makra podobnej do funkcji. 
1. Przenosi on do następujących tokenów i znajduje `ECHO` wywoływanego przez funkcję, która jest wywoływana: `ECHO(("Hello", "World"))`, która rozwija się do `("Hello", "World")`
1. `IMPL1` nigdy nie jest ponownie brana pod uwagę dla rozwinięcia, więc pełny wynik rozwinięcia to: `IMPL1("Hello", "World");`

Makro można zmodyfikować tak, aby zachowywały się tak samo pod eksperymentalnym preprocesorem i tradycyjną preprocesorem przez dodanie w innej warstwie operatora pośredni:

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

Eksperymentalny preprocesor jest przede wszystkim kompletny, mimo że niektóre logiki dyrektywy preprocesora nadal powraca do tradycyjnego zachowania. Oto częściowa lista niekompletnych funkcji:

- Obsługa `_Pragma`
- Funkcje języka c++ 20
- Zwiększ usterkę blokującą: operatory logiczne w wyrażeniach stałych preprocesora nie są w pełni zaimplementowane w nowym preprocesorze. W przypadku niektórych dyrektyw `#if` nowy preprocesor może wrócić do tradycyjnego preprocesora. Efekt jest zauważalny tylko wtedy, gdy makra, które są niezgodne z tradycyjną preprocesorem, zostaną rozwinięte, co może nastąpić podczas kompilowania miejsc preprocesora.
