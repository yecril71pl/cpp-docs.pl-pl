---
title: LNK2019 błędu narzędzi konsolidatora
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 3c4e5578c7b0f496feb4d40933af624f462a31d2
ms.sourcegitcommit: 680a155cc44a38f88bb2b1c5a1ef6dcb7141c011
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252625"
---
# <a name="linker-tools-error-lnk2019"></a>LNK2019 błędu narzędzi konsolidatora

nierozpoznany symbol zewnętrzny "*symbol*" przywoływany w funkcji "*Function*"

Skompilowany kod dla *funkcji* wykonuje odwołanie lub wywołanie do *symbolu*, ale ten symbol nie jest zdefiniowany w żadnej z bibliotek lub plików obiektów określonych dla konsolidatora.

Ten komunikat o błędzie następuje po błędzie krytycznym [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Aby naprawić błąd LNK1120, należy naprawić wszystkie błędy LNK2001 i LNK2019.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów na uzyskanie tego błędu, ale wszystkie z nich obejmują odwołanie do funkcji lub zmiennej, którą nie może *rozpoznać*konsolidator, lub znaleźć definicję dla. Kompilator może określić, kiedy symbol nie jest *zadeklarowany*, ale nie, gdy nie jest *zdefiniowany*, ponieważ definicja może znajdować się w innym pliku lub bibliotece źródłowej. Jeśli symbol jest określany, ale nigdy nie zdefiniowany, konsolidator generuje nierozpoznany błąd symbolu zewnętrznego.

Poniżej przedstawiono niektóre typowe problemy, które powodują LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Plik lub biblioteka obiektu, która zawiera definicję symbolu, nie jest połączona

W programie Visual Studio Sprawdź, czy plik źródłowy, który zawiera definicję, został skompilowany i połączony jako część projektu. W wierszu polecenia upewnij się, że plik źródłowy, który zawiera definicję, jest kompilowany i że utworzony plik obiektu zostanie uwzględniony na liście plików do połączenia.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklaracja symbolu nie jest taka sama jak definicja symbolu

Sprawdź, czy pisownia i wielkie litery są używane zarówno w deklaracji, jak i w definicji, i wszędzie tam, gdzie symbol jest używany lub wywoływana.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Używana jest funkcja, ale typ lub liczba parametrów nie są zgodne z definicją funkcji

Deklaracja funkcji musi być zgodna z definicją. Sprawdź, czy wywołanie funkcji jest zgodne z deklaracją i czy deklaracja jest zgodna z definicją. Kod, który wywołuje funkcje szablonu, musi również mieć zgodne deklaracje funkcji szablonu, które zawierają te same parametry szablonu, jak definicja. Przykład niezgodności deklaracji szablonu zawiera przykład LNK2019e. cpp w sekcji przykładów.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkcja lub zmienna jest zadeklarowana, ale nie jest zdefiniowana

Zazwyczaj oznacza to, że deklaracja istnieje w pliku nagłówkowym, ale nie zaimplementowano pasującej definicji. W przypadku funkcji Członkowskich lub statycznych elementów członkowskich danych implementacja musi zawierać selektor zakresu klas. Aby zapoznać się z przykładem, zobacz sekcję [brakująca treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konwencja wywoływania różni się między deklaracją funkcji a definicją funkcji

Konwencje wywoływania ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)lub [__vectorcall](../../cpp/vectorcall.md)) są kodowane jako część nazwy dekoracyjnej. Sprawdź, czy Konwencja wywoływania jest taka sama.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol jest zdefiniowany w pliku C, ale deklarowany bez użycia extern "C" w C++ pliku

Symbole zdefiniowane w pliku, który jest kompilowany jako C mają różne nazwy dekoracyjne niż symbole zadeklarowane C++ w pliku, chyba że jest używany zewnętrzny modyfikator ["C"](../../cpp/using-extern-to-specify-linkage.md) . Sprawdź, czy deklaracja pasuje do powiązania kompilacji dla każdego symbolu. Podobnie, jeśli zdefiniujesz symbol w C++ pliku, który będzie używany przez program C, użyj `extern "C"` w definicji.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol jest definiowany jako statyczny, a następnie przywoływany poza plikiem

W C++, w przeciwieństwie do języka C, [globalne stałe](../../error-messages/tool-errors/global-constants-in-cpp.md) mają powiązania `static`. Aby obejść to ograniczenie, można uwzględnić inicjalizacje `const` w pliku nagłówkowym i dołączyć ten nagłówek do plików. cpp lub można wprowadzić zmienną niestałą i użyć do niej dostępu stałego.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Statyczny element członkowski klasy nie jest zdefiniowany

Statyczny element członkowski klasy musi mieć unikatową definicję lub narusza regułę z jedną definicją. Statyczny element członkowski klasy, który nie może być zdefiniowany w tekście, musi być zdefiniowany w jednym pliku źródłowym przy użyciu jego w pełni kwalifikowanej nazwy. Jeśli nie jest on zdefiniowany, konsolidator generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Zależność kompilacji jest definiowana tylko jako zależność projektu w rozwiązaniu

W starszych wersjach programu Visual Studio wystarcza ten poziom zależności. Jednak począwszy od programu Visual Studio 2010, program Visual Studio wymaga [odwołania projektu do projektu](/visualstudio/ide/managing-references-in-a-project). Jeśli projekt nie ma odwołania projekt-projekt, może wystąpić błąd konsolidatora. Dodaj odwołanie projekt-projekt, aby je usunąć.

### <a name="an-entry-point-is-not-defined"></a>Punkt wejścia nie jest zdefiniowany

Kod aplikacji musi definiować odpowiedni punkt wejścia: `main` lub `wmain` dla aplikacji konsolowych, `WinMain` lub `wWinMain` dla aplikacji systemu Windows. Aby uzyskać więcej informacji, zobacz [Main: Uruchamianie programu](../../cpp/main-program-startup.md) lub [Funkcja WinMain](/windows/win32/api/winbase/nf-winbase-winmain). Aby użyć niestandardowego punktu wejścia, określ opcję konsolidatora [/entry (symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md) . 

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Tworzenie aplikacji konsolowej przy użyciu ustawień dla aplikacji systemu Windows

Jeśli komunikat o błędzie przypomina **nierozpoznany symbol zewnętrzny WinMain przywoływany w funkcji** *function_name*, link przy użyciu **/SUBSYSTEM: Console** zamiast **/SUBSYSTEM: Windows**. Aby uzyskać więcej informacji na temat tego ustawienia i instrukcje dotyczące sposobu ustawiania tej właściwości w programie Visual Studio, zobacz [/subsystem (Określ podsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Podjęto próbę połączenia bibliotek 64-bitowych z 32-bitowym kodem lub 32-bitowych bibliotek do kodu 64-bitowego

Biblioteki i pliki obiektów połączone z kodem muszą być kompilowane dla tej samej architektury, w której znajduje się kod. Sprawdź, czy biblioteki, do których odwołuje się projekt, są kompilowane dla tej samej architektury co projekt. Upewnij się, że opcja ścieżki [/LIBPATH](../../build/reference/libpath-additional-libpath.md) lub **Dodatkowe katalogi bibliotek** używana przez konsolidator wskazuje na biblioteki skompilowane dla właściwej architektury.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>W różnych plikach źródłowych można używać różnych opcji kompilatora.

Używanie wbudowanych funkcji zdefiniowanych w plikach. cpp i mieszanie opcji kompilatora w celu wyróżnienia funkcji w różnych plikach źródłowych może spowodować LNK2019. Aby uzyskać więcej informacji, zobacz temat [problemy z wykreśleniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Używasz zmiennych automatycznych poza ich zakresem

Automatyczne zmienne (zakres funkcji) mogą być używane tylko w zakresie tej funkcji. Te zmienne nie mogą być deklarowane `extern` i używane w innych plikach źródłowych. Aby zapoznać się z przykładem, zobacz [Automatyczne zmienne (zakres funkcji)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Wywoływanie funkcji instrinsic lub przekazywanie typów argumentów do funkcji wewnętrznych, które nie są obsługiwane w architekturze docelowej

Na przykład jeśli używasz wewnętrznego AVX2, ale nie określisz opcji kompilatora [/arch: AVX2](../../build/reference/arch-x86.md) , kompilator zakłada, że wewnętrzna jest funkcją zewnętrzną. Zamiast generować wbudowaną instrukcję, kompilator generuje wywołanie do zewnętrznego symbolu o takiej samej nazwie jak wewnętrzna. Gdy konsolidator próbuje znaleźć definicję brakującej funkcji, generuje LNK2019. Sprawdź, czy używane są tylko elementy wewnętrzne i typy obsługiwane przez architekturę docelową.

### <a name="you-mix-code-that-uses-native-wchar_t-with-code-that-doesnt"></a>Mieszać kod, który używa natywnego WCHAR @ no__t-0T z kodem, który nie

C++zgodność z językiem, która została wykonana w programie Visual Studio 2005 `wchar_t` domyślnie typem natywnym. Musisz użyć opcji [/Zc: wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Compiler, aby wygenerować kod zgodny z bibliotekami i plikami obiektów skompilowanymi przy użyciu wcześniejszych wersji programu Visual Studio. Jeśli nie wszystkie pliki zostały skompilowane przy użyciu tego samego **/Zc: WCHAR @ no__t-1T** , odwołania do typów mogą nie być rozpoznawane jako zgodne typy. Sprawdź, czy typy `wchar_t` we wszystkich bibliotekach i plikach obiektów są zgodne, aktualizując typy, które są używane, lub używając spójnych ustawień **/Zc: wchar_t** podczas kompilowania.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i Vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, należy rozważyć użycie [Vcpkg](../../vcpkg.md), Menedżera pakietów Visual C++ Package, aby zainstalować i skompilować bibliotekę. Program Vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports), a także ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz odpowiedni wpis w [blogu wizualnym C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) .

## <a name="diagnosis-tools"></a>Narzędzia diagnostyczne

Może być trudne, aby określić, dlaczego konsolidator nie może znaleźć określonej definicji symbolu. Często problem polega na tym, że nie dołączono kodu, który zawiera definicję w kompilacji, lub opcje kompilacji stworzyły różne nazwy dekoracyjne symboli zewnętrznych. Istnieje kilka narzędzi i opcji, które mogą pomóc zdiagnozować błąd LNK2019.

- Opcja konsolidatora [/verbose](../../build/reference/verbose-print-progress-messages.md) może pomóc określić, które pliki są przywoływane przez konsolidator. Może to pomóc w sprawdzeniu, czy plik, który zawiera definicję symbolu, jest uwzględniony w kompilacji.

- Opcje [/exports](../../build/reference/dash-exports.md) i [/Symbols](../../build/reference/symbols.md) narzędzia **polecenia DUMPBIN** mogą pomóc w ustaleniu, które symbole są zdefiniowane w plikach dll i obiektach biblioteki. Sprawdź, czy eksportowane nazwy dekoracyjne pasują do dekoracyjnych nazw, które wyszukuje konsolidator.

- Narzędzie **UNDNAME** może wyświetlić odpowiedni, niedekoracyjny symbol zewnętrzny dla nazwy dekoracyjnej.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów kodu, które powodują błąd LNK2019, wraz z informacjami dotyczącymi sposobu usuwania błędu.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol jest zadeklarowany, ale nie został zdefiniowany

W tym przykładzie zmienna zewnętrzna jest zadeklarowana, ale nie jest zdefiniowana:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Oto inny przykład, w którym zmienna i funkcja są zadeklarowane jako `extern`, ale nie podano definicji:

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

Jeśli `i` i `g` są zdefiniowane w jednym z plików zawartych w kompilacji, konsolidator generuje LNK2019. Błędy można naprawić, dołączając plik kodu źródłowego, który zawiera definicje w ramach kompilacji. Alternatywnie można przekazać pliki. obj lub. lib, które zawierają definicje do konsolidatora.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Statyczny element członkowski danych jest zadeklarowany, ale nie został zdefiniowany

LNK2019 może również wystąpić, gdy statyczny element członkowski danych jest zadeklarowany, ale nie został zdefiniowany. Poniższy przykład generuje LNK2019 i pokazuje, jak rozwiązać ten problem.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Parametry deklaracji nie są zgodne z definicją

Kod, który wywołuje funkcje szablonu, musi mieć zgodne deklaracje funkcji szablonu. Deklaracje muszą zawierać takie same parametry szablonu, jak definicja. Poniższy przykład generuje LNK2019 w operatorze zdefiniowanym przez użytkownika i pokazuje, jak rozwiązać ten problem.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
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

### <a name="inconsistent-wchar_t-type-definitions"></a>Niespójne definicje typów wchar_t

Ten przykład tworzy plik DLL, który ma eksport, który używa `WCHAR`, który jest rozpoznawany jako `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Następny przykład używa biblioteki DLL w poprzednim przykładzie i generuje LNK2019, ponieważ typy unsigned Short * i WCHAR @ no__t-0 nie są takie same.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Aby naprawić ten błąd, Zmień `unsigned short` na `wchar_t` lub `WCHAR` lub skompiluj LNK2019g. cpp przy użyciu **/Zc: wchar_t-** .

## <a name="additional-resources"></a>Zasoby dodatkowe

Aby uzyskać więcej informacji na temat możliwych przyczyn i rozwiązań dla programu LNK2001, zobacz pytanie Stack Overflow, [co to jest błąd niezdefiniowanego odwołania/nierozpoznany symbol zewnętrzny i jak go naprawić?](https://stackoverflow.com/q/12573816/2002113).

