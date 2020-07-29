---
title: Błąd narzędzi konsolidatora LNK2019
description: Wszystkie informacje o Microsoft Visual Studio konsolidatora LNK2019 i sposobach ich diagnozowania i poprawiania w kodzie C i C++.
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(WinMain):::'
- ':::no-loc(wmain):::'
- ':::no-loc(wWinMain):::'
- ':::no-loc(__cdecl):::'
- ':::no-loc(__stdcall):::'
- ':::no-loc(__fastcall):::'
- ':::no-loc(__vectorcall):::'
- ':::no-loc(extern):::'
- ':::no-loc(static):::'
- ':::no-loc(const):::'
- ':::no-loc(ARCH):::'
- ':::no-loc(AVX2):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(VERBOSE):::'
- ':::no-loc(EXPORTS):::'
- ':::no-loc(SYMBOLS):::'
- ':::no-loc(DUMPBIN):::'
- ':::no-loc(UNDNAME):::'
ms.openlocfilehash: b83ed3663e6b199e0f3384f6d30cb1c87c0e52c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219810"
---
# <a name="linker-tools-error-lnk2019"></a>Błąd narzędzi konsolidatora LNK2019

> nierozpoznany :::no-loc(extern)::: element Al symbol "*symbol*" przywoływany w funkcji "*Function*"

Skompilowany kod dla *funkcji* wykonuje odwołanie lub wywołanie do *symbolu*, ale konsolidator nie może znaleźć definicji symbolu w żadnej z bibliotek lub plików obiektów do powiązania.

Ten komunikat o błędzie następuje po błędzie krytycznym [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Aby naprawić błąd LNK1120, należy najpierw usunąć wszystkie błędy LNK2001 i LNK2019.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów na uzyskanie tego błędu. Wszystkie z nich obejmują odwołanie do funkcji lub zmiennej, których konsolidator nie może *rozpoznać*, lub znaleźć definicję dla. Kompilator może określić, kiedy symbol nie jest *zadeklarowany*, ale nie może stwierdzić, kiedy symbol nie jest *zdefiniowany*. Dzieje się tak, ponieważ definicja może znajdować się w innym pliku lub bibliotece źródłowej. Jeśli symbol jest określany, ale nigdy nie zdefiniowany, konsolidator generuje błąd nierozpoznanego :::no-loc(extern)::: symbolu Al.

Poniżej przedstawiono niektóre typowe problemy, które powodują LNK2019:

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>Plik źródłowy, który zawiera definicję symbolu nie został skompilowany

W programie Visual Studio upewnij się, że plik źródłowy, który definiuje symbol, zostanie skompilowany w ramach projektu. Sprawdź katalog wyjściowy kompilacji pośredniej dla odpowiadającego pliku. obj. Jeśli plik źródłowy nie jest kompilowany, kliknij prawym przyciskiem myszy plik w Eksplorator rozwiązań a następnie wybierz **Właściwości** , aby sprawdzić właściwości pliku. Na stronie Ogólne **Właściwości konfiguracji**  >  **General** powinna być wyświetlana wartość **Typ elementu** **kompilatora C/C++**. W wierszu polecenia upewnij się, że plik źródłowy, który zawiera definicję, został skompilowany.

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>Plik lub biblioteka obiektu, która zawiera definicję symbolu, nie jest połączona

W programie Visual Studio upewnij się, że plik lub biblioteka obiektu, która zawiera definicję symbolu, jest połączona w ramach projektu. W wierszu polecenia upewnij się, że lista plików do połączenia obejmuje plik lub bibliotekę obiektu.

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklaracja symbolu nie jest identyczna z definicją symbolu

Upewnij się, że używasz prawidłowej pisowni i wielkich liter w deklaracji i definicji, i wszędzie tam, gdzie symbol jest używany lub wywoływana.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>Funkcja jest używana, ale typ lub liczba parametrów nie pasują do definicji funkcji

Deklaracja funkcji musi być zgodna z definicją. Upewnij się, że wywołanie funkcji pasuje do deklaracji i że deklaracja jest zgodna z definicją. Kod, który wywołuje funkcje szablonu, musi również mieć zgodne deklaracje funkcji szablonu, które zawierają te same parametry szablonu, jak definicja. Przykład niezgodności deklaracji szablonu zawiera przykład LNK2019e. cpp w sekcji przykładów.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkcja lub zmienna jest zadeklarowana, ale nie jest zdefiniowana

LNK2019 może wystąpić, gdy deklaracja istnieje w pliku nagłówkowym, ale nie zaimplementowano pasującej definicji. W przypadku funkcji Członkowskich lub :::no-loc(static)::: elementów członkowskich danych implementacja musi zawierać selektor zakresu klas. Aby zapoznać się z przykładem, zobacz sekcję [brakująca treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konwencja wywoływania różni się między deklaracją funkcji a definicją funkcji

Konwencje wywoływania ( [:::no-loc(__cdecl):::](../../cpp/cdecl.md) , [:::no-loc(__stdcall):::](../../cpp/stdcall.md) , [:::no-loc(__fastcall):::](../../cpp/fastcall.md) lub [:::no-loc(__vectorcall):::](../../cpp/vectorcall.md) ) są kodowane jako część nazwy dekoracyjnej. Upewnij się, że Konwencja wywoływania jest taka sama.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>Symbol jest zdefiniowany w pliku C, ale zadeklarowany bez użycia :::no-loc(extern)::: "C" w pliku C++

Symbole zdefiniowane w pliku, który jest kompilowany jako C mają różne nazwy dekoracyjne niż symbole zadeklarowane w pliku języka C++, chyba że jest używany modyfikator [ :::no-loc(extern)::: "C"](../../cpp/using-:::no-loc(extern):::-to-specify-linkage.md) . Upewnij się, że deklaracja pasuje do powiązania kompilacji dla każdego symbolu. Podobnie, jeśli zdefiniujesz symbol w pliku języka C++, który będzie używany przez program C, użyj `:::no-loc(extern)::: "C"` w definicji.

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>Symbol jest zdefiniowany jako :::no-loc(static)::: , a następnie przywoływany poza plikiem

W języku C++, w przeciwieństwie do języka C, [globalne :::no-loc(const)::: ANTS](../../error-messages/tool-errors/global-:::no-loc(const):::ants-in-cpp.md) mają **`:::no-loc(static):::`** powiązania. Aby obejść to ograniczenie, można uwzględnić **`:::no-loc(const):::`** inicjalizacje w pliku nagłówkowym i dołączyć ten nagłówek do plików. cpp lub można utworzyć zmienną :::no-loc(const)::: nieant i użyć :::no-loc(const)::: odwołania ANT, aby uzyskać do niego dostęp.

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>:::no-loc(static):::Składowa klasy nie jest zdefiniowana

:::no-loc(static):::Składowa klasy musi mieć unikatową definicję lub narusza regułę z jedną definicją. :::no-loc(static):::Składowa klasy, która nie może być zdefiniowana w tekście, musi być zdefiniowana w jednym pliku źródłowym przy użyciu jego w pełni kwalifikowanej nazwy. Jeśli nie jest on zdefiniowany w ogóle, konsolidator generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Zależność kompilacji jest definiowana tylko jako zależność projektu w rozwiązaniu

W starszych wersjach programu Visual Studio wystarcza ten poziom zależności. Jednak począwszy od programu Visual Studio 2010, program Visual Studio wymaga [odwołania projektu do projektu](/visualstudio/ide/managing-references-in-a-project). Jeśli projekt nie zawiera odwołania do projektu, może wystąpić błąd konsolidatora. Dodaj odwołanie projekt-projekt, aby je usunąć.

### <a name="an-entry-point-isnt-defined"></a>Punkt wejścia nie jest zdefiniowany

Kod aplikacji musi definiować odpowiedni punkt wejścia: `:::no-loc(main):::` lub `:::no-loc(wmain):::` dla aplikacji konsolowych i `:::no-loc(WinMain):::` lub `:::no-loc(wWinMain):::` dla aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [ :::no-loc(main)::: funkcje i argumenty wiersza polecenia](../../cpp/:::no-loc(main):::-function-command-line-args.md) lub [ :::no-loc(WinMain)::: funkcję](/windows/win32/api/winbase/nf-winbase-win:::no-loc(main):::). Aby użyć niestandardowego punktu wejścia, określ opcję konsolidatora [/entry (symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) .

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Tworzenie aplikacji konsolowej przy użyciu ustawień dla aplikacji systemu Windows

Jeśli komunikat o błędzie przypomina **nierozpoznany :::no-loc(extern)::: symbol Al :::no-loc(WinMain)::: przywoływany w funkcji** *function_name*, link przy użyciu **/SUBSYSTEM: Console** zamiast **/SUBSYSTEM: Windows**. Aby uzyskać więcej informacji na temat tego ustawienia i instrukcje dotyczące sposobu ustawiania tej właściwości w programie Visual Studio, zobacz [/subsystem (Określ podsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Podjęto próbę połączenia bibliotek 64-bitowych z 32-bitowym kodem lub 32-bitowych bibliotek do kodu 64-bitowego

Biblioteki i pliki obiektów połączone z kodem muszą być kompilowane dla tej samej architektury, w której znajduje się kod. Upewnij się, że biblioteki, do których odwołuje się projekt, są kompilowane dla tej samej architektury co projekt. Upewnij się, że właściwość [/LIBPATH](../../build/reference/libpath-additional-libpath.md) lub **Dodatkowe katalogi bibliotek** wskazuje biblioteki skompilowane dla właściwej architektury.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>W różnych plikach źródłowych można używać różnych opcji kompilatora.

Używanie wbudowanych funkcji zdefiniowanych w plikach. cpp i mieszanie opcji kompilatora w celu wyróżnienia funkcji w różnych plikach źródłowych może spowodować LNK2019. Aby uzyskać więcej informacji, zobacz temat [problemy z wykreśleniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Używasz zmiennych automatycznych poza ich zakresem

Automatyczne zmienne (zakres funkcji) mogą być używane tylko w zakresie tej funkcji. Te zmienne nie mogą być zadeklarowane **`:::no-loc(extern):::`** i używane w innych plikach źródłowych. Aby zapoznać się z przykładem, zobacz [Automatyczne zmienne (zakres funkcji)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>Wywoływanie funkcji wewnętrznych lub przekazywanie typów argumentów do funkcji wewnętrznych, które nie są obsługiwane w architekturze docelowej

Na przykład jeśli używasz :::no-loc(AVX2)::: wewnętrznego, ale [ / :::no-loc(ARCH)::: :::no-loc(AVX2)::: ](../../build/reference/arch-x86.md) nie określisz opcji kompilatora, kompilator zakłada, że wewnętrzna jest :::no-loc(extern)::: funkcją Al. Zamiast generować wbudowaną instrukcję, kompilator generuje wywołanie do :::no-loc(extern)::: symbolu Al o takiej samej nazwie jak wewnętrzna. Gdy konsolidator próbuje znaleźć definicję brakującej funkcji, generuje LNK2019. Upewnij się, że używasz tylko elementów wewnętrznych i typów obsługiwanych przez architekturę docelową.

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>Mieszać kod, który używa natywnego :::no-loc(wchar_t)::: kodu, który nie

Zgodność języka C++, która została wykonana w programie Visual Studio 2005, domyślnie wprowadziła **`:::no-loc(wchar_t):::`** typ natywny. Jeśli nie wszystkie pliki zostały skompilowane przy użyciu tego samego **/Zc: :::no-loc(wchar_t)::: ** Settings, odwołania do typów mogą nie być rozpoznawane jako zgodne typy. Upewnij się **`:::no-loc(wchar_t):::`** , że typy we wszystkich bibliotekach i plikach obiektów są zgodne. Aktualizacja z elementu **`:::no-loc(wchar_t):::`** typedef lub użycie spójnej **/Zc: :::no-loc(wchar_t)::: ** Settings podczas kompilowania.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, należy rozważyć użycie [vcpkg](../../vcpkg.md), Menedżera pakietów języka C++, aby zainstalować i skompilować bibliotekę. vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports). Ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu.

## <a name="diagnosis-tools"></a>Narzędzia diagnostyczne

Czasami trudno jest określić, dlaczego konsolidator nie może znaleźć określonej definicji symbolu. Często problem polega na tym, że kod, który zawiera definicję w kompilacji, nie został uwzględniony. Lub opcje kompilacji stworzyły różne nazwy dekoracyjne :::no-loc(extern)::: symboli Al. Istnieje kilka narzędzi i opcji, które mogą ułatwić zdiagnozowanie błędów LNK2019.

- [/:::no-loc(VERBOSE):::](../../build/reference/verbose-print-progress-messages.md)Opcja konsolidatora może pomóc określić, które pliki są przywoływane przez konsolidator. Ta opcja może pomóc w sprawdzeniu, czy plik, który zawiera definicję symbolu, jest uwzględniony w kompilacji.

- [/:::no-loc(EXPORTS):::](../../build/reference/dash-exports.md)Opcje i [/:::no-loc(SYMBOLS):::](../../build/reference/symbols.md) **:::no-loc(DUMPBIN):::** narzędzia mogą pomóc w ustaleniu, które symbole są zdefiniowane w plikach dll i obiektach biblioteki. Upewnij się, że eksportowane nazwy dekoracyjne pasują do dekoracyjnych nazw, które wyszukuje konsolidator.

- **:::no-loc(UNDNAME):::** Narzędzie może wyświetlić odpowiednik niedekoracyjnego :::no-loc(extern)::: symbolu Al dla nazwy dekoracyjnej.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów kodu, które powodują błąd LNK2019, wraz z informacjami dotyczącymi sposobu usuwania błędu.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol jest zadeklarowany, ale nie został zdefiniowany

W tym przykładzie :::no-loc(extern)::: zmienna Al jest zadeklarowana, ale nie jest zdefiniowana:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
:::no-loc(extern)::: char B[100];   // B isn't available to the linker
int :::no-loc(main):::() {
   B[0] = ' ';   // LNK2019
}
```

Oto inny przykład, w którym zmienna i funkcja są zadeklarowane jako, **`:::no-loc(extern):::`** ale nie podano definicji:

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
:::no-loc(extern)::: int i;
:::no-loc(extern)::: void g();
void f() {
   i++;
   g();
}
int :::no-loc(main):::() {}
```

Jeśli `i` i nie `g` są zdefiniowane w jednym z plików zawartych w kompilacji, KONSOLIDATOR generuje LNK2019. Błędy można naprawić, dołączając plik kodu źródłowego, który zawiera definicje w ramach kompilacji. Alternatywnie można przekazać pliki. obj lub. lib, które zawierają definicje do konsolidatora.

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>:::no-loc(static):::Element członkowski danych jest zadeklarowany, ale nie został zdefiniowany

LNK2019 może również wystąpić, gdy :::no-loc(static)::: element członkowski danych jest zadeklarowany, ale nie został zdefiniowany. Poniższy przykład generuje LNK2019 i pokazuje, jak rozwiązać ten problem.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   :::no-loc(static)::: int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int :::no-loc(main):::() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-dont-match-the-definition"></a>Parametry deklaracji nie pasują do definicji

Kod, który wywołuje funkcje szablonu, musi mieć zgodne deklaracje funkcji szablonu. Deklaracje muszą zawierać takie same parametry szablonu, jak definicja. Poniższy przykład generuje LNK2019 w operatorze zdefiniowanym przez użytkownika i pokazuje, jak rozwiązać ten problem.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int :::no-loc(main):::() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved :::no-loc(extern):::al
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>Niespójne :::no-loc(wchar_t)::: definicje typów

Ten przykład tworzy bibliotekę DLL, która korzysta z eksportu, który jest `WCHAR` rozpoznawany jako **`:::no-loc(wchar_t):::`** .

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to :::no-loc(wchar_t):::
__declspec(dllexport) void func(WCHAR*) {}
```

Następny przykład używa biblioteki DLL w poprzednim przykładzie i generuje LNK2019, ponieważ typy `unsigned short*` i `WCHAR*` nie są takie same.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int :::no-loc(main):::() {
   func(0);
}
```

Aby naprawić ten błąd, Zmień **`unsigned short`** na **`:::no-loc(wchar_t):::`** lub `WCHAR` Skompiluj LNK2019g. cpp przy użyciu **/Zc :::no-loc(wchar_t)::: - :**.

## <a name="additional-resources"></a>Zasoby dodatkowe

Aby uzyskać więcej informacji na temat możliwych przyczyn i rozwiązań dla programu LNK2001, zobacz pytanie Stack Overflow, [co to jest błąd niezdefiniowanego odwołania/nierozpoznany :::no-loc(extern)::: symbol Al i jak rozwiązać ten problem?](https://stackoverflow.com/q/12573816/2002113).
