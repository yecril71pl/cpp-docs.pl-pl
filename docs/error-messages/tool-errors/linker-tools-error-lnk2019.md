---
title: Błąd narzędzi konsolidatora LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: 0ef0bfd565b8c76816cc1f8a20b1521da238cdfc
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447707"
---
# <a name="linker-tools-error-lnk2019"></a>Błąd narzędzi konsolidatora LNK2019

Nierozpoznany symbol zewnętrzny "*symbol*"przywoływany w funkcji"*funkcja*"

Skompilowany kod *funkcja* sprawia, że odwołanie lub wywołanie *symbol*, ale ta symbol nie jest zdefiniowany w żadnym z biblioteki lub określono konsolidatora plików obiektów.

Ten komunikat o błędzie następuje błąd krytyczny [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Należy naprawić wszystkie LNK2001 i LNK2019 błędów, aby naprawić błąd LNK1120.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów, aby uzyskać ten błąd, ale wszystkie z nich obejmują odwołania do funkcji lub zmienna, która nie konsolidator *rozwiązać*, lub znaleźć definicję. Kompilator może wskazywać, gdy nie jest symbolem *zadeklarowana*, ale nie Jeśli nie zostanie *zdefiniowane*, ponieważ definicja może znajdować się w innym plikiem źródłowym lub biblioteki. Jeśli symbol jest określone, ale nigdy nie jest zdefiniowany, konsolidator generuje błąd nierozpoznany symbol zewnętrzny.

Poniżej przedstawiono niektóre typowe problemy powodujące LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Plik obiektu lub biblioteki, który zawiera definicję symbolu nie został połączony.

W programie Visual Studio Sprawdź, czy plik źródłowy, który zawiera definicję jest skompilowane i połączone w ramach projektu. W wierszu polecenia Sprawdź, czy plik źródłowy, który zawiera definicję jest kompilowany i że wynikowy plik obiektu znajduje się lista plików, połączyć.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklaracja symbolu nie została wpisana taka sama jak definicji symbolu

Sprawdź błędu pisowni i wielkości liter, jest używany zarówno w deklaracji i definicji i wszędzie tam, gdzie używane lub o nazwie symbolu.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Funkcja jest używana, ale typ lub liczba parametrów nie są zgodne w definicji funkcji

Deklaracja funkcji musi być zgodny definicją. Sprawdź, czy wywołanie funkcji jest zgodna deklaracja i że deklaracja jest zgodna z definicją. Kod, który wywołuje funkcje szablonu musi mieć również dopasowywanie deklaracji funkcji szablonu, które zawierają te same parametry szablonu jako definicji. Na przykład w przypadku niezgodności deklaracji szablonu zobacz przykładową LNK2019e.cpp w sekcji przykładów.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkcja lub zmienna jest zadeklarowana ale niezdefiniowana

Zwykle oznacza to, deklarację istnieje w pliku nagłówkowym, ale brak pasujących definicji jest zaimplementowana. Dla funkcji składowych lub elementów członkowskich danych statycznych implementacja musi zawierać selektor zakres klasy. Aby uzyskać przykład, zobacz [Brak treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konwencja wywoływania różni się od deklaracji funkcji i definicji funkcji

Konwencje wywoływania ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md), lub [__vectorcall](../../cpp/vectorcall.md)) są zakodowane jako część nazwy dekoracyjne. Sprawdź, czy konwencja wywołania jest taka sama.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol jest zdefiniowana w pliku C, ale zadeklarowana bez użycia extern "C" w pliku języka C++

Symbole zdefiniowane w pliku, który jest kompilowany jako C mają różne nazwy dekoracyjne niż symbole zadeklarowanych w pliku języka C++, chyba że używasz [extern "C"](../../cpp/using-extern-to-specify-linkage.md) modyfikator. Sprawdź, czy deklaracja jest zgodna z powiązaniem kompilacji dla każdego symbolu. Podobnie, jeśli symbol jest zdefiniowana w pliku C++, który będzie używany przez C program, użyj `extern "C"` w definicji.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol został zdefiniowany jako statyczny i później przywoływane poza plikiem

W języku C++, w przeciwieństwie do języka C [stałe globalne](../../error-messages/tool-errors/global-constants-in-cpp.md) mają `static` powiązania. Aby obejść to ograniczenie, można dołączyć `const` inicjalizacje w nagłówku pliku i dołączyć ten nagłówek w plikach CPP lub ustaw dla zmiennej niestałe i użyj stałe odwołanie do niego dostęp.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Nie zdefiniowano statycznej składowej klasy

Członek klasy statycznej musi mieć unikatowy definicji lub go będzie naruszenia reguły jednej definicji. Element członkowski klasy statycznej, który nie może być zdefiniowano w tekście musi być zdefiniowany w jednym pliku źródłowym przy użyciu jego w pełni kwalifikowana nazwa. Jeśli nie jest zdefiniowana w ogóle, konsolidator generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Zależność kompilacji jest zdefiniowana tylko jako zależność projektu w rozwiązaniu

We wcześniejszych wersjach programu Visual Studio ten poziom zależności była wystarczająca. Począwszy od programu Visual Studio 2010, Visual Studio wymaga jednak [odwołania projekt projekt](/visualstudio/ide/managing-references-in-a-project). Jeśli projekt nie ma odwołania projekt projekt, otrzymasz ten błąd konsolidatora. Dodaj odwołanie projektu do projektu, aby rozwiązać ten problem.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Tworzenie aplikacji konsolowej przy użyciu ustawień dla aplikacji Windows

Jeśli komunikat o błędzie jest podobny do **nierozpoznany symbol zewnętrzny WinMain przywoływany w funkcji** *nazwa_funkcji*, link przy użyciu **opcji** zamiast **/Subsystem: Windows**. Aby uzyskać więcej informacji na temat tego ustawienia i w jaki sposób ustawić tę właściwość w programie Visual Studio, zobacz [/Subsystem (Określ podsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Spróbuj połączyć 64-bitowych bibliotek kodu 32-bitowego lub 32-bitowych bibliotek kodu 64-bitowego

Biblioteki i pliki obiektów powiązany kod musi być skompilowana dla taką samą architekturę jako kod. Upewnij się, że biblioteki odwołania projektu są kompilowane dla taką samą architekturę co projekt. Upewnij się, że [/libpath —](../../build/reference/libpath-additional-libpath.md) lub **dodatkowe katalogi bibliotek** ścieżki opcji używanych przez punkty konsolidatora do bibliotek stworzona z myślą o architektury.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Użyj różne opcje kompilatora dla funkcji wbudowanie w innych plików źródłowych

Za pomocą funkcji śródwierszowych zdefiniowane w plikach CPP i mieszanie funkcja wbudowanie opcje kompilatora w innych plików źródłowych może spowodować, że LNK2019. Aby uzyskać więcej informacji, zobacz [problemy ze Śródwierszowaniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>W przypadku używania zmiennych automatycznych poza ich zakresem

Automatyczne zmienne (zakresem funkcji) należy używać tylko w zakresie tej funkcji. Nie można zadeklarować zmienne `extern` i używane w innych plikach źródłowych. Aby uzyskać przykład, zobacz [automatyczne zmienne (związane z zakresem funkcji)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Wywoływanie funkcji instrinsic lub przekazać typy argumentów do funkcje wewnętrzne, które nie są obsługiwane dla docelowej architektury

Na przykład, jeśli korzystasz AVX2 wewnętrznej, ale nie należy określać [/ARCH:AVX2](../../build/reference/arch-x86.md) — opcja kompilatora, kompilator zakłada, że wewnętrznych jest funkcją zewnętrzną. Zamiast generowania instrukcję wbudowane, kompilator generuje wywołanie symbol zewnętrzny z taką samą nazwę jak wewnętrznych. Próba Znajdź definicję tę funkcję, brak przez konsolidator generuje LNK2019. Sprawdź, czy używasz tylko funkcje wewnętrzne i typy obsługiwane przez architektury docelowej.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Mieszanie kod używający natywnej wchar\_t z kodem, który nie

C++język zgodność pracy, która została wykonana w programie Visual Studio 2005 wprowadzone `wchar_t` typu natywnego domyślnie. Należy użyć [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) — opcja kompilatora do generowania kodu zgodne z plikami biblioteki i obiektu skompilowane przy użyciu starszych wersji programu Visual Studio. Jeśli nie wszystkie pliki zostały skompilowane, korzystając z tych samych **/Zc:wchar\_t** ustawienia, typ odwołania nie mogą prowadzić do zgodnych typów. Upewnij się, że `wchar_t` typów we wszystkich plikach do biblioteki i obiektu są zgodne, aktualizując typy, które są używane, lub przy użyciu spójnego **/Zc:** ustawienia podczas kompilowania.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteki innych firm i Vcpkg

Jeśli zostanie wyświetlony ten błąd, jeśli próbujesz skonfigurować biblioteki innych firm w ramach kompilacji, należy rozważyć użycie [Vcpkg](../../vcpkg.md), do Visual C++ Menedżera pakietów, instalowanie i tworzenie biblioteki. Vcpkg obsługująca duży i rosnący [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports)i ustawia właściwości konfiguracji i zależności wymagane do pomyślnej kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz powiązane [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) wpis.

## <a name="diagnosis-tools"></a>Narzędzia do diagnostyki

Może być trudno stwierdzić, dlaczego konsolidator nie można odnaleźć definicji określonego symbolu. Często problem jest, że nie wprowadzono kodu, który zawiera definicję w kompilacji lub kompilacji, utworzonych przez opcje innej dekorowane nazwy zewnętrzne symbole. Istnieją różne narzędzia i opcje, które mogą pomóc Ci diagnozowanie błędów LNK2019.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) — opcja konsolidatora może pomóc w określeniu, plików, których odwołania konsolidatora. Może to ułatwić możesz sprawdzić, czy plik, który zawiera definicję symbolu znajduje się w kompilacji.

- [/EKSPORTUJE](../../build/reference/dash-exports.md) i [/symbole](../../build/reference/symbols.md) opcje **DUMPBIN** narzędzie może pomóc odkryć, symboli, które są zdefiniowane w plikach dll i obiektu lub biblioteki. Sprawdź wyeksportowany dekorowane odpowiada nazwy dekoracyjne konsolidator nazwy wyszukuje.

- **UNDNAME** narzędzia można wyświetlić równoważne niedekorowanego symbolu zewnętrznego dla nazwy dekoracyjne.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów kodu, który powoduje, że to błąd LNK2019 wraz z informacjami o tym, jak naprawić błąd.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol jest zadeklarowana ale niezdefiniowana

W tym przykładzie zewnętrznej zmiennej jest zadeklarowana ale niezdefiniowana:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Oto inny przykład, w którym zmiennych i funkcji są deklarowane jako `extern` dostarczono nie definicji:

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

Chyba że `i` i `g` są definiowane w jednym z plików znajdujących się w kompilacji, konsolidator generuje LNK2019. Przez dołączenie pliku kodu źródłowego, który zawiera definicje jako część kompilacji, można naprawić błędy. Alternatywnie można przekazać pliki .obj lub pliki .lib, które zawierają definicje do konsolidatora.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Element członkowski danych statycznych jest zadeklarowana ale niezdefiniowana

LNK2019 może również wystąpić, gdy element członkowski danych statycznych jest zadeklarowana ale niezdefiniowana. Poniższy przykład generuje LNK2019 i pokazuje, jak go naprawić.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Deklaracji parametrów nie pasują do definicji

Kod, który wywołuje funkcje szablonu muszą mieć, dopasowanie deklaracji funkcji szablonu. Deklaracje mogą zawierać te same parametry szablonu jako definicji. Poniższy przykład generuje LNK2019 na zdefiniowany przez użytkownika operator i pokazuje, jak go naprawić.

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

### <a name="inconsistent-wchart-type-definitions"></a>Niespójne wchar_t definicji typu

Ten przykład umożliwia utworzenie biblioteki DLL, która ma eksportu, która używa `WCHAR`, która jest rozpoznawana jako `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Następny przykład korzysta z biblioteki DLL w poprzednim przykładzie, a następnie generuje LNK2019, ponieważ typy unsigned short * i WCHAR\* nie są takie same.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Aby naprawić ten błąd, zmień `unsigned short` do `wchar_t` lub `WCHAR`, lub Kompiluj LNK2019g.cpp przy użyciu **/Zc:wchar_t-**.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji na temat możliwych przyczyn i rozwiązań dla LNK2001 zobacz pytanie dotyczące przepełnienia stosu [co to jest błąd zewnętrzny symbol Niezdefiniowany odwołania/nierozpoznanych i jak go naprawić?](http://stackoverflow.com/q/12573816/2002113).

