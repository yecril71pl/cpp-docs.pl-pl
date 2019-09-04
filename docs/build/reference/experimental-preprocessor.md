---
title: '/Experimental: preprocesor (Włącz tryb zgodności preprocesora)'
description: Użyj opcji kompilatora preprocesora/Experimental:, aby włączyć obsługę kompilatora eksperymentalnego dla preprocesora, który jest zgodny ze standardem.
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294422"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/Experimental: preprocesor (Włącz tryb zgodności preprocesora)

Ta opcja włącza eksperymentalny, oparty na tokenach proces preprocesora, który jest zgodny ze standardami języka C++ 11, w tym funkcjami preprocesora C99.

## <a name="syntax"></a>Składnia

> **/Experimental: preprocesor** [ **-** ]

## <a name="remarks"></a>Uwagi

Użyj opcji kompilatora **preprocesora/Experimental:** , aby włączyć eksperymentalny preprocesor. Możesz użyć **/Experimental: preprocesor-** Option, aby jawnie określić tradycyjny preprocesor.

Opcja **/Experimental: preprocesora** jest dostępna w programie Visual Studio 2017 w wersji 15,8.

Możesz wykryć, który preprocesor jest używany w czasie kompilacji. Sprawdź wartość wstępnie zdefiniowanego makra [ \_\_MSVC tradycyjną](../../preprocessor/predefined-macros.md) , aby stwierdzić, czy tradycyjny preprocesor jest w użyciu. To makro jest ustawiane bezwarunkowo przez wersje kompilatora, które go obsługują, niezależnie od tego, który preprocesora jest wywoływany. Jej wartość jest równa 1 dla tradycyjnego preprocesora. Jest to 0 w przypadku zgodnego preprocesora doświadczalnego:

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>Zmiany zachowania w eksperymentalnym preprocesorze

Poniżej przedstawiono niektóre typowe zmiany, które można napotkać, gdy tryb zgodności preprocesora jest włączony:

#### <a name="macro-comments"></a>Komentarze makr

Tradycyjny preprocesor używa buforów znaków zamiast tokenów preprocesora. Pozwala to na pewne nietypowe zachowanie, takie jak niezależny komentarz preprocesora:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>Prefiksy ciągu (L # Val)

Tradycyjny preprocesor niepoprawnie łączy prefiks ciągu z wynikiem [operatora tworzenia ciągu (#)](../../preprocessor/stringizing-operator-hash.md):

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

`L` Prefiks jest niezbędny w tym miejscu, ponieważ sąsiadujące literały ciągu są łączone po rozwinięciu tego makra. Poprawka zgodna z poprzednimi wersjami ma na celu zmianę definicji na:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Ten problem znajduje się również w wygodnych makrach, które "łańcuchujący" argumentem do szerokiego literału ciągu:

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>Ostrzeżenie dla nieprawidłowego ##

Gdy [operator wklejania tokenu (# #)](../../preprocessor/token-pasting-operator-hash-hash.md) nie powoduje pojedynczego prawidłowego tokenu przetwarzania wstępnego, zachowanie jest niezdefiniowane. Tradycyjny preprocesor w trybie dyskretnym nie może połączyć tokenów. Nowy preprocesor jest zgodny z zachowaniem większości innych kompilatorów i emituje diagnostykę.

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>Dla koprocedury przecinków w makrach wariadyczne

Rozważmy następujący przykład:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

Wszystkie główne kompilatory mają rozszerzenie preprocesora, które pomaga rozwiązać ten problem. Tradycyjny preprocesor MSVC zawsze usuwa przecinki przed pustymi `__VA_ARGS__` zamiennikami. Zaktualizowany preprocesor jest bardziej blisko zachowaniem innych popularnych kompilatorów międzyplatformowych. Aby można było usunąć przecinek, argument wariadyczne musi być braku, a nie tylko pusty i musi być oznaczony `##` operatorem:

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

W nadchodzącym standardzie C + + 2a ten problem został rozwiązany przez `__VA_OPT__`dodanie, który nie został jeszcze zaimplementowany.

#### <a name="macro-arguments-are-unpacked"></a>Argumenty makr są "rozpakowane"

W tradycyjnych preprocesorach, jeśli makro przekazuje jeden z argumentów do innego makra zależnego, argument nie zostanie "rozpakowany", gdy zostanie zastąpiony. Zwykle Ta optymalizacja nie jest zauważalna, ale może prowadzić do nietypowego zachowania:

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

Podczas rozszerzania `A()`tradycyjny preprocesor przekazuje wszystkie argumenty spakowane w `__VA_ARGS__` `TWO_STRINGS`do pierwszego argumentu. Argument `TWO_STRINGS` wariadyczne jest pusty, co powoduje, że `#first` wynik `"1, 2"` jest raczej, a nie tylko `"1"`. Być może zastanawiasz się, co się stało z `#__VA_ARGS__` wynikami w tradycyjnym rozszerzeniu preprocesora. Jeśli parametr wariadyczne jest pusty, powinien wynikać z pustym literałem ciągu "". Z powodu oddzielnego problemu nie Wygenerowano pustego tokenu literału ciągu.

#### <a name="rescanning-replacement-list-for-macros"></a>Ponowne skanowanie listy zastępczej dla makr

Po wymianie makra powstające tokeny są ponownie skanowane pod kątem dodatkowych identyfikatorów makr, które mają zostać zastąpione. Algorytm ponownego skanowania używany przez tradycyjny preprocesor nie jest zgodny, jak pokazano w tym przykładzie na podstawie rzeczywistego kodu:

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

Aby zobaczyć, co się dzieje w tym przykładzie, rozbicie rozwinięcia rozpoczyna się `DO_THING`od:

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

Drugi, kot jest rozwinięty:

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

Który umieszcza tokeny w tym stanie:

`IMPL1 ECHO(("Hello", "World"))`

Preprocesor wyszukuje identyfikator `IMPL1`makra podobnej do funkcji, ale nie następuje znak "(", więc nie jest uważany za wywołanie makra podobnej do funkcji. Przechodzi do następujących tokenów i znajduje makro `ECHO` podobne do funkcji wywoływane:

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`nigdy nie jest ponownie brany pod uwagę dla rozwinięcia, więc pełny wynik rozwinięcia to:

`IMPL1("Hello", "World");`

Makro może być modyfikowane tak samo jak w przypadku eksperymentalnego preprocesora i tradycyjnego preprocesora. Rozwiązaniem jest dodanie kolejnej warstwy operatora pośredni:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>Zgodność trybu zgodności

Eksperymentalny preprocesor nie został jeszcze ukończony, a niektóre logika dyrektywy preprocesora nadal powraca do tradycyjnego zachowania. Oto częściowa lista niekompletnych funkcji:

- Obsługa`_Pragma`
- Funkcje języka c++ 20
- Dodatkowe ulepszenia diagnostyki
- Przełącza kontrolowanie danych wyjściowych w obszarze/E i/P
- Zwiększ usterkę blokującą: Operatory logiczne w wyrażeniach stałych preprocesora nie są w pełni zaimplementowane w nowym preprocesorze. W przypadku `#if` niektórych dyrektyw nowy preprocesor może wrócić do tradycyjnego preprocesora. Efekt jest zauważalny tylko wtedy, gdy makra, które są niezgodne z tradycyjną preprocesorem, zostaną rozwinięte, co może nastąpić podczas kompilowania miejsc preprocesora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **C/C++**  > **wiersz polecenia** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Experimental: preprocesora** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
