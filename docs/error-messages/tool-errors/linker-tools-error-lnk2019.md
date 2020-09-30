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
- main
- WinMain
- wmain
- wWinMain
- __cdecl
- __stdcall
- __fastcall
- __vectorcall
- extern
- static
- const
- ARCH
- AVX2
- wchar_t
- VERBOSE
- EXPORTS
- SYMBOLS
- DUMPBIN
- UNDNAME
ms.openlocfilehash: d09e232b934761d138fee7324c462c915d919959
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509739"
---
# <a name="linker-tools-error-lnk2019"></a>Błąd narzędzi konsolidatora LNK2019

> nierozpoznany extern element Al symbol "*symbol*" przywoływany w funkcji "*Function*"

Skompilowany kod dla *funkcji* wykonuje odwołanie lub wywołanie do *symbolu*, ale konsolidator nie może znaleźć definicji symbolu w żadnej z bibliotek lub plików obiektów do powiązania.

Ten komunikat o błędzie następuje po błędzie krytycznym [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Aby naprawić błąd LNK1120, należy najpierw usunąć wszystkie błędy LNK2001 i LNK2019.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów na uzyskanie tego błędu. Wszystkie z nich obejmują odwołanie do funkcji lub zmiennej, których konsolidator nie może *rozpoznać*, lub znaleźć definicję dla. Kompilator może określić, kiedy symbol nie jest *zadeklarowany*, ale nie może stwierdzić, kiedy symbol nie jest *zdefiniowany*. Dzieje się tak, ponieważ definicja może znajdować się w innym pliku lub bibliotece źródłowej. Jeśli symbol jest określany, ale nigdy nie zdefiniowany, konsolidator generuje błąd nierozpoznanego extern symbolu Al.

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

LNK2019 może wystąpić, gdy deklaracja istnieje w pliku nagłówkowym, ale nie zaimplementowano pasującej definicji. W przypadku funkcji Członkowskich lub static elementów członkowskich danych implementacja musi zawierać selektor zakresu klas. Aby zapoznać się z przykładem, zobacz sekcję [brakująca treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konwencja wywoływania różni się między deklaracją funkcji a definicją funkcji

Konwencje wywoływania ( [__cdecl](../../cpp/cdecl.md) , [__stdcall](../../cpp/stdcall.md) , [__fastcall](../../cpp/fastcall.md) lub [__vectorcall](../../cpp/vectorcall.md) ) są kodowane jako część nazwy dekoracyjnej. Upewnij się, że Konwencja wywoływania jest taka sama.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>Symbol jest zdefiniowany w pliku C, ale zadeklarowany bez użycia extern "C" w pliku C++

Symbole zdefiniowane w pliku, który jest kompilowany jako C mają różne nazwy dekoracyjne niż symbole zadeklarowane w pliku języka C++, chyba że jest używany modyfikator [ extern "C"](../../cpp/extern-cpp.md) . Upewnij się, że deklaracja pasuje do powiązania kompilacji dla każdego symbolu. Podobnie, jeśli zdefiniujesz symbol w pliku języka C++, który będzie używany przez program C, użyj `extern "C"` w definicji.

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>Symbol jest zdefiniowany jako static , a następnie przywoływany poza plikiem

W języku C++, w przeciwieństwie do języka C, [globalne const ANTS](../../error-messages/tool-errors/global-constants-in-cpp.md) mają **`static`** powiązania. Aby obejść to ograniczenie, można uwzględnić **`const`** inicjalizacje w pliku nagłówkowym i dołączyć ten nagłówek do plików. cpp lub można utworzyć zmienną const nieant i użyć const odwołania ANT, aby uzyskać do niego dostęp.

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>staticSkładowa klasy nie jest zdefiniowana

staticSkładowa klasy musi mieć unikatową definicję lub narusza regułę z jedną definicją. staticSkładowa klasy, która nie może być zdefiniowana w tekście, musi być zdefiniowana w jednym pliku źródłowym przy użyciu jego w pełni kwalifikowanej nazwy. Jeśli nie jest on zdefiniowany w ogóle, konsolidator generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Zależność kompilacji jest definiowana tylko jako zależność projektu w rozwiązaniu

W starszych wersjach programu Visual Studio wystarcza ten poziom zależności. Jednak począwszy od programu Visual Studio 2010, program Visual Studio wymaga [odwołania projektu do projektu](/visualstudio/ide/managing-references-in-a-project). Jeśli projekt nie zawiera odwołania do projektu, może wystąpić błąd konsolidatora. Dodaj odwołanie projekt-projekt, aby je usunąć.

### <a name="an-entry-point-isnt-defined"></a>Punkt wejścia nie jest zdefiniowany

Kod aplikacji musi definiować odpowiedni punkt wejścia: `main` lub `wmain` dla aplikacji konsolowych i `WinMain` lub `wWinMain` dla aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [ main funkcje i argumenty wiersza polecenia](../../cpp/main-function-command-line-args.md) lub [ WinMain funkcję](/windows/win32/api/winbase/nf-winbase-winmain). Aby użyć niestandardowego punktu wejścia, określ opcję konsolidatora [/entry (symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) .

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Tworzenie aplikacji konsolowej przy użyciu ustawień dla aplikacji systemu Windows

Jeśli komunikat o błędzie przypomina **nierozpoznany extern symbol Al WinMain przywoływany w funkcji** *function_name*, link przy użyciu **/SUBSYSTEM: Console** zamiast **/SUBSYSTEM: Windows**. Aby uzyskać więcej informacji na temat tego ustawienia i instrukcje dotyczące sposobu ustawiania tej właściwości w programie Visual Studio, zobacz [/subsystem (Określ podsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Podjęto próbę połączenia bibliotek 64-bitowych z 32-bitowym kodem lub 32-bitowych bibliotek do kodu 64-bitowego

Biblioteki i pliki obiektów połączone z kodem muszą być kompilowane dla tej samej architektury, w której znajduje się kod. Upewnij się, że biblioteki, do których odwołuje się projekt, są kompilowane dla tej samej architektury co projekt. Upewnij się, że właściwość [/LIBPATH](../../build/reference/libpath-additional-libpath.md) lub **Dodatkowe katalogi bibliotek** wskazuje biblioteki skompilowane dla właściwej architektury.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>W różnych plikach źródłowych można używać różnych opcji kompilatora.

Używanie wbudowanych funkcji zdefiniowanych w plikach. cpp i mieszanie opcji kompilatora w celu wyróżnienia funkcji w różnych plikach źródłowych może spowodować LNK2019. Aby uzyskać więcej informacji, zobacz temat [problemy z wykreśleniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Używasz zmiennych automatycznych poza ich zakresem

Automatyczne zmienne (zakres funkcji) mogą być używane tylko w zakresie tej funkcji. Te zmienne nie mogą być zadeklarowane **`extern`** i używane w innych plikach źródłowych. Aby zapoznać się z przykładem, zobacz [Automatyczne zmienne (zakres funkcji)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>Wywoływanie funkcji wewnętrznych lub przekazywanie typów argumentów do funkcji wewnętrznych, które nie są obsługiwane w architekturze docelowej

Na przykład jeśli używasz AVX2 wewnętrznego, ale [ / ARCH AVX2 ](../../build/reference/arch-x86.md) nie określisz opcji kompilatora, kompilator zakłada, że wewnętrzna jest extern funkcją Al. Zamiast generować wbudowaną instrukcję, kompilator generuje wywołanie do extern symbolu Al o takiej samej nazwie jak wewnętrzna. Gdy konsolidator próbuje znaleźć definicję brakującej funkcji, generuje LNK2019. Upewnij się, że używasz tylko elementów wewnętrznych i typów obsługiwanych przez architekturę docelową.

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>Mieszać kod, który używa natywnego wchar_t kodu, który nie

Zgodność języka C++, która została wykonana w programie Visual Studio 2005, domyślnie wprowadziła **`wchar_t`** typ natywny. Jeśli nie wszystkie pliki zostały skompilowane przy użyciu tego samego **/Zc: wchar_t ** Settings, odwołania do typów mogą nie być rozpoznawane jako zgodne typy. Upewnij się **`wchar_t`** , że typy we wszystkich bibliotekach i plikach obiektów są zgodne. Aktualizacja z elementu **`wchar_t`** typedef lub użycie spójnej **/Zc: wchar_t ** Settings podczas kompilowania.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, należy rozważyć użycie [vcpkg](../../build/vcpkg.md), Menedżera pakietów języka C++, aby zainstalować i skompilować bibliotekę. vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports). Ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu.

## <a name="diagnosis-tools"></a>Narzędzia diagnostyczne

Czasami trudno jest określić, dlaczego konsolidator nie może znaleźć określonej definicji symbolu. Często problem polega na tym, że kod, który zawiera definicję w kompilacji, nie został uwzględniony. Lub opcje kompilacji stworzyły różne nazwy dekoracyjne extern symboli Al. Istnieje kilka narzędzi i opcji, które mogą ułatwić zdiagnozowanie błędów LNK2019.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)Opcja konsolidatora może pomóc określić, które pliki są przywoływane przez konsolidator. Ta opcja może pomóc w sprawdzeniu, czy plik, który zawiera definicję symbolu, jest uwzględniony w kompilacji.

- [/EXPORTS](../../build/reference/dash-exports.md)Opcje i [/SYMBOLS](../../build/reference/symbols.md) **DUMPBIN** narzędzia mogą pomóc w ustaleniu, które symbole są zdefiniowane w plikach dll i obiektach biblioteki. Upewnij się, że eksportowane nazwy dekoracyjne pasują do dekoracyjnych nazw, które wyszukuje konsolidator.

- **UNDNAME** Narzędzie może wyświetlić odpowiednik niedekoracyjnego extern symbolu Al dla nazwy dekoracyjnej.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów kodu, które powodują błąd LNK2019, wraz z informacjami dotyczącymi sposobu usuwania błędu.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol jest zadeklarowany, ale nie został zdefiniowany

W tym przykładzie extern zmienna Al jest zadeklarowana, ale nie jest zdefiniowana:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Oto inny przykład, w którym zmienna i funkcja są zadeklarowane jako, **`extern`** ale nie podano definicji:

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

Jeśli `i` i nie `g` są zdefiniowane w jednym z plików zawartych w kompilacji, KONSOLIDATOR generuje LNK2019. Błędy można naprawić, dołączając plik kodu źródłowego, który zawiera definicje w ramach kompilacji. Alternatywnie można przekazać pliki. obj lub. lib, które zawierają definicje do konsolidatora.

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>staticElement członkowski danych jest zadeklarowany, ale nie został zdefiniowany

LNK2019 może również wystąpić, gdy static element członkowski danych jest zadeklarowany, ale nie został zdefiniowany. Poniższy przykład generuje LNK2019 i pokazuje, jak rozwiązać ten problem.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
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

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>Niespójne wchar_t definicje typów

Ten przykład tworzy bibliotekę DLL, która korzysta z eksportu, który jest `WCHAR` rozpoznawany jako **`wchar_t`** .

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Następny przykład używa biblioteki DLL w poprzednim przykładzie i generuje LNK2019, ponieważ typy `unsigned short*` i `WCHAR*` nie są takie same.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Aby naprawić ten błąd, Zmień **`unsigned short`** na **`wchar_t`** lub `WCHAR` Skompiluj LNK2019g. cpp przy użyciu **/Zc wchar_t - :**.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji na temat możliwych przyczyn i rozwiązań dla programu LNK2001, zobacz pytanie Stack Overflow, [co to jest błąd niezdefiniowanego odwołania/nierozpoznany extern symbol Al i jak rozwiązać ten problem?](https://stackoverflow.com/q/12573816/2002113).
