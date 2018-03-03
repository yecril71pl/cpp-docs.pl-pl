---
title: "Błąd narzędzi konsolidatora LNK2019 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20f6fdad0d26d04c6e8022f7b29dbdd7f13ac874
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2019"></a>Błąd narzędzi konsolidatora LNK2019

Nierozpoznany zewnętrzny symbol "*symbol*"przywoływany w funkcji"*funkcja*"

Skompilowany kod *funkcja* sprawia, że odwołanie lub wywołanie *symbol*, ale ten symbol nie jest zdefiniowany w żadnym z biblioteki lub określono do konsolidatora plików obiektów.

Ten komunikat o błędzie następuje błąd krytyczny [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Należy naprawić wszystkie LNK2001 i LNK2019 błędów, aby naprawić błąd LNK1120.

## <a name="possible-causes"></a>Możliwe przyczyny

Istnieje wiele sposobów, aby uzyskać ten błąd, ale dotyczą wszystkich z nich odwołanie do funkcji lub zmienna, która nie konsolidator *rozwiązać*, lub znaleźć definicji. Kompilator może wskazywać, gdy nie jest symbolem *zadeklarowany*, ale nie po nie jest *zdefiniowane*, ponieważ definicja może znajdować się w innym plikiem źródłowym lub biblioteki. Jeśli symbol jest określone, ale nigdy nie jest zdefiniowany, konsolidator generuje błąd nierozpoznany zewnętrzny symbol.

Poniżej przedstawiono niektóre typowe problemy, które powodują LNK2019:

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Plik obiektu lub biblioteki, który zawiera definicję symbolu nie jest połączony.

W programie Visual Studio Sprawdź, czy plik źródłowy, który zawiera definicję jest skompilowany i połączone w ramach projektu. W wierszu polecenia Sprawdź kompilowania pliku źródłowego, który zawiera definicję i czy plik wynikowy obiekt znajduje się lista plików, aby połączyć.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>Deklaracja symbolu nie została wpisana taka sama jak definicji symbolu

Sprawdź poprawną pisownię i wielkość liter jest używany w deklaracji i definicji i wszędzie tam, gdzie symbol jest używany, lub o nazwie.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Używana jest funkcja, ale typ lub liczba parametrów nie są zgodne z definicji funkcji

Deklaracja funkcji muszą być zgodne definicji. Sprawdź, czy wywołanie funkcji jest zgodna deklaracja i czy deklaracja jest zgodna z definicji. Kod, który wywołuje funkcje szablonu musi mieć również dopasowania szablonu deklaracje funkcji, które obejmują takie same parametry szablonu jako definicji. Na przykład niezgodność deklaracji szablonu Zobacz przykład LNK2019e.cpp w sekcji przykładów.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Funkcja lub zmienna jest zadeklarowana ale niezdefiniowana

Zwykle oznacza to, deklaracji istnieje w pliku nagłówka, ale brak pasujących definicji jest zaimplementowana. Do funkcji Członkowskich lub statyczne elementy członkowskie danych implementacja musi zawierać selektor zakres klasy. Na przykład zobacz [Brak treść funkcji lub zmienna](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Konwencja wywoływania różni się między deklaracji funkcji i definicji funkcji

Konwencje wywoływania ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md), lub [__vectorcall](../../cpp/vectorcall.md)) są zakodowane jako część nazwa. Sprawdź, czy Konwencja wywoływania jest taka sama.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Symbol zdefiniowany w pliku C, ale zadeklarowana bez użycia zewnętrzne "C" w pliku języka C++

Symbole zdefiniowane w pliku, który ma być kompilowana c mieć różne nazwy ozdobione niż symbole zadeklarowany w pliku języka C++, chyba że są używane [zewnętrzne "C"](../../cpp/using-extern-to-specify-linkage.md) modyfikator. Sprawdź, czy deklaracja jest zgodna z powiązaniem kompilacji dla każdego symbolu. Podobnie, jeśli symbol jest zdefiniowana w pliku języka C++, który będzie używany przez C program, użyj `extern "C"` w definicji.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Symbol jest zdefiniowany jako statyczne i później przywoływany poza plikiem

W języku C++, w odróżnieniu od C [stałe globalne](../../error-messages/tool-errors/global-constants-in-cpp.md) ma `static` połączenie. Aby uniknąć problemów tego ograniczenia, mogą obejmować `const` inicjacjach w nagłówku pliku i obejmują nagłówka w plikach CPP lub ustaw dla zmiennej z systemem innym niż stała i użyj stałej odwołania do niego dostęp.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Statyczny element członkowski klasy nie jest zdefiniowany.

Element członkowski klasy statyczne muszą mieć unikatowe definicji lub będzie narusza reguły jednej definicji. Element członkowski klasy statycznej, który nie może być zdefiniowano w tekście musi być zdefiniowana w jeden plik źródłowy przy użyciu w pełni kwalifikowaną nazwę. Jeśli nie jest on zdefiniowany w ogóle, konsolidator generuje LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Zależność kompilacji jest zdefiniowana tylko jako zależność projektu w rozwiązaniu

We wcześniejszych wersjach programu Visual Studio ten poziom zależności jest wystarczające. Począwszy od programu Visual Studio 2010, Visual Studio wymaga jednak [odwołania projektu do projektu](/visualstudio/ide/managing-references-in-a-project). Jeśli projekt nie ma odwołanie projektu do projektu, może zostać wyświetlony ten błąd konsolidatora. Dodaj odwołanie projektu do projektu, aby go rozwiązać.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Tworzenie aplikacji konsoli przy użyciu ustawień dla aplikacji systemu Windows

Jeśli komunikat o błędzie jest podobny do **nierozpoznany zewnętrzny symbol WinMain przywoływany w funkcji** *nazwa_funkcji*, łącza, za pomocą **opcji** zamiast **/Subsystem: Windows**. Aby uzyskać więcej informacji na temat tego ustawienia i w jaki sposób ustawić tę właściwość w programie Visual Studio, zobacz [/Subsystem (Określ podsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Próba połączyć 64-bitowych bibliotek kodu 32-bitowego lub 32-bitowych bibliotek do kodu 64-bitowych

Biblioteki i połączone z kodu plików obiektów muszą być skompilowane dla taką samą architekturę jako kodu. Sprawdź, czy biblioteki odwołania projektu są kompilowane dla taką samą architekturę jako projektu. Upewnij się, że [/libpath](../../build/reference/libpath-additional-libpath.md) lub **dodatkowe katalogi bibliotek** opcję Ścieżka używanych przez punkty konsolidatora do bibliotek skompilowany dla architektury.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Użyj innych opcji kompilatora ze śródwierszowaniem funkcji w plikach źródłowych różnych

Przy użyciu funkcji śródwierszowych zdefiniowane w plikach CPP i mieszanie funkcja ze śródwierszowaniem opcje kompilatora w plikach źródłowych różnych może spowodować LNK2019. Aby uzyskać więcej informacji, zobacz [problemy ze Śródwierszowaniem funkcji](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>W przypadku używania zmiennych automatycznych spoza ich zakresu

Automatyczne zmienne (zakresem funkcji) można używać tylko w zakresie tej funkcji. Nie można zadeklarować zmienne `extern` i używane w innych plikach źródłowych. Na przykład zobacz [automatyczne zmienne (związane z zakresem funkcji)](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Wywołanie funkcji instrinsic lub przekazania typy argumentów do funkcji wewnętrznych, które nie są obsługiwane na architektury docelowej

Na przykład używać AVX2 wewnętrznej, ale nie określono [/ARCH:AVX2](../../build/reference/arch-x86.md) — opcja kompilatora, kompilator zakłada, że wewnętrznej funkcji zewnętrznej. Zamiast generowania instrukcji wbudowany, kompilator generuje wywołanie zewnętrzny symbol o tej samej nazwie jako wewnętrzne. Próba definicja to Brak funkcji przez konsolidator generuje LNK2019. Sprawdź, że używane funkcje wewnętrzne i typy obsługiwanych przez architektury docelowej.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Mieszać kod, który używa natywnego wchar\_t z kodem, który nie

Pracy zgodność języka C++, która została wykonana w Visual C++ 2005 wprowadzone `wchar_t` typu macierzystego domyślnie. Należy użyć [/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) opcję kompilatora, aby wygenerować kod zgodny z biblioteki i obiekt plików skompilowanych przy użyciu wcześniejszej wersji programu Visual C++. Jeśli nie wszystkie pliki zostały skompilowane przy użyciu takie same **/Zc:wchar\_t** ustawienia, typu odwołania nie może rozpoznać niezgodne typy. Sprawdź, czy `wchar_t` typów we wszystkich plikach biblioteki i obiektu są zgodne, aktualizując typy, które są używane lub przy użyciu spójnej **/Zc:** ustawień podczas kompilowania.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteki innych firm i Vcpkg

Jeśli zostanie wyświetlony ten błąd, gdy chcesz skonfigurować bibliotekę innych firm w ramach systemu, należy rozważyć użycie [Vcpkg](../../vcpkg.md), Visual C++ Menedżera pakietów, aby zainstalować i tworzenie biblioteki. Vcpkg obsługuje duży i rosnącym [listy bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports)i ustawia właściwości konfiguracji i zależności wymagane dla pomyślnej kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz pokrewne [Visual C++ blogu](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="diagnosis-tools"></a>Narzędzia diagnostyki

Może być trudne dowiedzieć się, dlaczego konsolidator nie można odnaleźć definicji określonego symbolu. Często ten problem nie kod, który zawiera definicję w kompilacji nie zostały uwzględnione, lub kompilacji, które opcje zostały utworzone w różnych dekorowane nazwy dla symboli zewnętrznych. Istnieje kilka narzędzi i opcji, które mogą ułatwić diagnozowanie błędów LNK2019.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) — opcja konsolidatora może pomóc w określeniu, które pliki odwołania konsolidatora. Ułatwia to sprawdzić, czy plik zawierający definicję tego symbolu jest dołączony do kompilacji.

- [/EKSPORTUJE](../../build/reference/dash-exports.md) i [/symbole](../../build/reference/symbols.md) opcje **DUMPBIN** narzędzia ułatwiają odnajdywanie symbole, które są zdefiniowane w plików dll i obiektu lub biblioteki. Sprawdź wyeksportowany dekorowane nazwy ozdobione konsolidator nazwy wyszukuje odpowiada.

- **UNDNAME** narzędzia można wyświetlić równoważne bez symboli zewnętrznych dla nazwy ozdobione.

## <a name="examples"></a>Przykłady

Oto kilka przykładów kodu, który powoduje błąd LNK2019, wraz z informacjami o tym, jak naprawić błąd.

### <a name="a-symbol-is-declared-but-not-defined"></a>Symbol jest zadeklarowana ale niezdefiniowana

W tym przykładzie zewnętrznych zmienna jest zadeklarowana ale niezdefiniowana:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Kolejny przykład, w którym zmiennych i funkcji są deklarowane jako `extern` dostarczono nie definicji:

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

O ile `i` i `g` są zdefiniowane w jednym z plików znajdujących się w kompilacji, konsolidator generuje LNK2019. Aby naprawić błędy, należy w tym pliku kodu źródłowego, który zawiera definicje kompilacji w ramach. Alternatywnie można przekazać pliki obj lub lib pliki, które zawierają definicje, aby konsolidator.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Parametry deklaracji są niezgodne z definicji

Kod, który wywołuje funkcje szablonu musi mieć pasujące deklaracje funkcji szablonu. Deklaracje musi zawierać te same parametry szablonu jako definicji. Poniższy przykład generuje LNK2019 na operatorem zdefiniowane przez użytkownika i pokazuje, jak go naprawić.

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

Ten przykład tworzy bibliotekę DLL, która ma eksportu, która używa `WCHAR`, który jest rozpoznawany jako `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Następna próbka korzysta z biblioteki DLL w poprzednim przykładzie, a następnie generuje LNK2019, ponieważ typy bez znaku krótkiej * i WCHAR\* nie są takie same.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

 Aby naprawić ten błąd, należy zmienić `unsigned short` do `wchar_t` lub `WCHAR`, lub skompiluj LNK2019g.cpp przy użyciu **/Zc:wchar_t-**.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać więcej informacji o możliwe przyczyny i rozwiązania LNK2001, zobacz pytanie przepełnienie stosu [co to jest błąd zewnętrzny symbol Niezdefiniowany odwołanie/nierozpoznane i jak go naprawić?](http://stackoverflow.com/q/12573816/2002113).

