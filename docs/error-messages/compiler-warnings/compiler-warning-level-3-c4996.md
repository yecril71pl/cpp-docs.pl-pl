---
title: Ostrzeżenie kompilatora (poziom 3) C4996
description: Wyjaśnia, dlaczego C4996 jest ostrzeżenie kompilatora i zawiera opis czynności, które należy wykonać.
ms.date: 07/09/2020
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 9f834c548b2a6b291304bdbf0082659577bfd694
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180984"
---
# <a name="compiler-warning-level-3-c4996"></a>Ostrzeżenie kompilatora (poziom 3) C4996

W kodzie jest używana funkcja, element członkowski klasy, zmienna lub element typedef, który jest oznaczony jako *przestarzały*. Symbole są przestarzałe przy użyciu [`__declspec(deprecated)`](../../cpp/deprecated-cpp.md) modyfikatora lub atrybutu c++ 14 [`[[deprecated]]`](../../cpp/attributes.md) . Rzeczywisty komunikat ostrzegawczy C4996 jest określany przez `deprecated` modyfikator lub atrybut deklaracji.

> [!IMPORTANT]
> To ostrzeżenie jest zawsze zamierzonym komunikatem z autora pliku nagłówkowego, który deklaruje symbol. Nie należy używać symbolu przestarzałego bez znajomości konsekwencji.

## <a name="remarks"></a>Uwagi

Wiele funkcji, funkcje składowe, funkcje szablonu i zmienne globalne w bibliotekach programu Visual Studio są *przestarzałe*. Niektóre, takie jak POSIX i funkcje specyficzne dla firmy Microsoft, są przestarzałe, ponieważ teraz mają inną preferowaną nazwę. Niektóre funkcje biblioteki środowiska uruchomieniowego języka C są przestarzałe, ponieważ są niezabezpieczone i mają bezpieczniejszy wariant. Inne są przestarzałe, ponieważ są przestarzałe. Komunikaty o zaniechaniu zwykle obejmują sugerowaną zastąpienie dla przestarzałej funkcji lub zmiennej globalnej.

## <a name="turn-off-the-warning"></a>Wyłącz ostrzeżenie

Aby rozwiązać problem z C4996, zwykle zalecamy zmianę kodu. Zamiast tego użyj sugerowanych funkcji i zmiennych globalnych. Jeśli konieczne jest użycie istniejących funkcji lub zmiennych z przyczyn związanych z przenośnością, można wyłączyć ostrzeżenie.

### <a name="turn-off-the-warning-for-a-specific-line-of-code"></a>Wyłącz ostrzeżenie dla określonego wiersza kodu

Aby wyłączyć Ostrzeżenie dla określonego wiersza kodu, użyj [`warning`](../../preprocessor/warning.md) dyrektywy pragma `#pragma warning(suppress : 4996)` .

### <a name="turn-off-the-warning-within-a-file"></a>Wyłącz ostrzeżenie w pliku

Aby wyłączyć ostrzeżenie w pliku dla wszystkiego, co następuje, użyj dyrektywy pragma warning, `#pragma warning(disable : 4996)` .

### <a name="turn-off-the-warning-in-command-line-builds"></a>Wyłącz ostrzeżenie w kompilacjach w wierszu polecenia

Aby wyłączyć ostrzeżenia globalnie w kompilacjach w wierszu polecenia, użyj [`/wd4996`](../../build/reference/compiler-option-warning-level.md) opcji wiersza polecenia.

### <a name="turn-off-the-warning-for-a-project-in-visual-studio"></a>Wyłącz ostrzeżenie dla projektu w programie Visual Studio

Aby wyłączyć Ostrzeżenie dla całego projektu w środowisku IDE programu Visual Studio:

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać informacje na temat korzystania z okna dialogowego strony właściwości, zobacz [strony właściwości](../../build/reference/property-pages-visual-cpp.md).

1. Wybierz stronę właściwości **Konfiguracja**  >  **C/C++**  >  **zaawansowana** C/C++.

1. Edytuj Właściwość **Wyłącz określone ostrzeżenia** , aby dodać *`4996`* . Wybierz **przycisk OK** , aby zastosować zmiany.

### <a name="disable-the-warning-using-preprocessor-macros"></a>Wyłącz ostrzeżenie przy użyciu makr preprocesora

Makra preprocesora można także użyć do wyłączenia niektórych określonych klas ostrzeżeń o zaniechaniu używanych w bibliotekach. Poniższe makra zostały opisane poniżej.

Aby zdefiniować makro preprocesora w programie Visual Studio:

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać informacje na temat korzystania z okna dialogowego strony właściwości, zobacz [strony właściwości](../../build/reference/property-pages-visual-cpp.md).

1. Rozwiń węzeł **Właściwości konfiguracji > C/C++ > preprocesor**.

1. We właściwości **Definicje preprocesora** Dodaj nazwę makra. Wybierz **przycisk OK** , aby zapisać, a następnie Skompiluj ponownie projekt.

Aby zdefiniować makro tylko w określonych plikach źródłowych, należy dodać wiersz, taki jak `#define EXAMPLE_MACRO_NAME` przed dowolnym wierszem zawierającym plik nagłówkowy.

Poniżej przedstawiono niektóre typowe źródła ostrzeżeń i błędów C4996:

## <a name="posix-function-names"></a>Nazwy funkcji POSIX

**`The POSIX name for this item is deprecated. Instead, use the ISO C and C++ conformant name:`** _`new-name.`_ **`See online help for details.`**

Firma Microsoft zmieniła nazwy niektórych funkcji opartych na systemie POSIX i określonej przez firmę Microsoft w ramach platformy CRT, aby zapewnić zgodność z ograniczeniami C99 i C++ 03 dla zarezerwowanych i globalnych nazw zdefiniowanych przez implementację. *Tylko nazwy są przestarzałe, a nie same funkcje*. W większości przypadków wiodący znak podkreślenia został dodany do nazwy funkcji w celu utworzenia zgodnej nazwy. Kompilator wystawia ostrzeżenie o wycofaniu oryginalnej nazwy funkcji i sugeruje preferowaną nazwę.

Aby rozwiązać ten problem, zwykle zalecamy zmianę kodu w celu użycia sugerowanych nazw funkcji. Zaktualizowane nazwy są jednak specyficzne dla firmy Microsoft. Jeśli musisz użyć istniejących nazw funkcji dla powodów związanych z przenośnością, możesz wyłączyć te ostrzeżenia. Funkcje są nadal dostępne w bibliotece pod ich oryginalnymi nazwami.

Aby wyłączyć ostrzeżenia o zaniechaniu dla tych funkcji, zdefiniuj makro preprocesora **`_CRT_NONSTDC_NO_WARNINGS`** . Możesz zdefiniować to makro w wierszu polecenia, dołączając opcję `/D_CRT_NONSTDC_NO_WARNINGS` .

## <a name="unsafe-crt-library-functions"></a>Niezabezpieczone funkcje biblioteki CRT

**`This function or variable may be unsafe. Consider using`** _`safe-version`_ **`instead. To disable deprecation, use _CRT_SECURE_NO_WARNINGS. See online help for details.`**

Firma Microsoft zaprzestarzała niektóre standardowe i Globals biblioteki CRT i C++, ponieważ dostępne są bezpieczniejsze wersje. Większość przestarzałych funkcji zezwala na niesprawdzone dostęp do odczytu lub zapisu do buforów. Ich niewłaściwe użycie może prowadzić do poważnych problemów z zabezpieczeniami. Kompilator wystawia ostrzeżenie o wycofaniu tych funkcji i sugeruje funkcję preferowaną.

Aby rozwiązać ten problem, zalecamy użycie funkcji lub zmiennej *`safe-version`* . Czasami nie jest to możliwe, w przypadku portów lub zgodności z poprzednimi wersjami. Należy uważnie sprawdzić, czy nie jest możliwe zastępowanie buforu lub przeczytanie go w kodzie. Następnie można wyłączyć ostrzeżenie.

Aby wyłączyć ostrzeżenia o zaniechaniu dla tych funkcji w CRT, zdefiniuj **`_CRT_SECURE_NO_WARNINGS`** .

Aby wyłączyć ostrzeżenia o przestarzałych zmiennych globalnych, zdefiniuj **`_CRT_SECURE_NO_WARNINGS_GLOBALS`** .

Aby uzyskać więcej informacji na temat tych przestarzałych funkcji i Globals, zobacz [funkcje zabezpieczeń w](../../c-runtime-library/security-features-in-the-crt.md) bibliotekach CRT i [Safe: standardowa biblioteka języka C++](../../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="unsafe-standard-library-functions"></a>Niebezpieczne funkcje biblioteki standardowej

**`'std::`** *`function_name`* **`::_Unchecked_iterators::_Deprecate' Call to std::`** *`function_name`* **`with parameters that may be unsafe - this call relies on the caller to check that the passed values are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation on how to use Visual C++ 'Checked Iterators'`**

W programie Visual Studio 2015 to ostrzeżenie jest wyświetlane w kompilacjach debugowania, ponieważ niektóre funkcje szablonu standardowej biblioteki języka C++ nie sprawdzają poprawności parametrów. Często jest to spowodowane brakiem wystarczającej ilości informacji do sprawdzenia granic kontenera. Lub, ponieważ Iteratory mogą być używane nieprawidłowo z funkcją. To ostrzeżenie pomaga zidentyfikować te funkcje, ponieważ mogą one być źródłem poważnych luk w zabezpieczeniach w programie. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../../standard-library/checked-iterators.md).

Na przykład to ostrzeżenie jest wyświetlane w trybie debugowania, Jeśli przekażesz wskaźnik elementu do `std::copy` , zamiast zwykłej tablicy. Aby rozwiązać ten problem, użyj odpowiednio zadeklarowanej tablicy, aby Biblioteka mogła sprawdzać zakresy tablicy i sprawdzać powiązana.

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

Kilka algorytmów standardowej biblioteki zostało zaktualizowanych w taki sposób, aby zawierały wersje "Dual Range" w języku C++ 14. Jeśli używasz wersji z podwójnym zakresem, drugi zakres zapewni wymagane sprawdzanie granic:

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

W tym przykładzie pokazano kilka sposobów, aby można było użyć standardowej biblioteki do sprawdzenia użycia iteratora i gdy niesprawdzone użycie może być niebezpieczne:

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

Jeśli sprawdzono, że kod nie może mieć błędu przepełnienia buforu, można wyłączyć to ostrzeżenie. Aby wyłączyć ostrzeżenia dla tych funkcji, zdefiniuj **`_SCL_SECURE_NO_WARNINGS`** .

## <a name="checked-iterators-enabled"></a>Sprawdzone Iteratory włączone

C4996 może również wystąpić, jeśli nie używasz sprawdzonego iteratora `_ITERATOR_DEBUG_LEVEL` , gdy jest zdefiniowany jako 1 lub 2. Jest ona domyślnie ustawiona na 2 dla kompilacji w trybie debugowania oraz do 0 dla kompilacji detalicznych. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../../standard-library/checked-iterators.md).

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

## <a name="unsafe-mfc-or-atl-code"></a>Niebezpieczny kod MFC lub ATL

C4996 może wystąpić, jeśli używasz funkcji MFC lub ATL, które były przestarzałe ze względów bezpieczeństwa.

Aby rozwiązać ten problem, zdecydowanie zalecamy zmianę kodu w taki sposób, aby korzystał z zaktualizowanych funkcji.

Aby uzyskać informacje na temat sposobu pomijania tych ostrzeżeń, zobacz [`_AFX_SECURE_NO_WARNINGS`](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings) .

## <a name="obsolete-crt-functions-and-variables"></a>Przestarzałe funkcje i zmienne CRT

**`This function or variable has been superseded by newer library or operating system functionality. Consider using`** *`new_item`* **`instead. See online help for details.`**

Niektóre funkcje biblioteki i zmienne globalne są przestarzałe jako przestarzałe. Te funkcje i zmienne mogą zostać usunięte w przyszłej wersji biblioteki. Kompilator wystawia ostrzeżenie o wycofaniu dla tych elementów i sugeruje preferowaną alternatywę.

Aby rozwiązać ten problem, zalecamy zmianę kodu w celu użycia sugerowanej funkcji lub zmiennej.

Aby wyłączyć ostrzeżenia o zaniechaniu dla tych elementów, zdefiniuj **`_CRT_OBSOLETE_NO_WARNINGS`** . Aby uzyskać więcej informacji, zapoznaj się z dokumentacją przestarzałej funkcji lub zmiennej.

## <a name="marshaling-errors-in-clr-code"></a>Kierowanie błędów w kodzie CLR

C4996 może również wystąpić w przypadku korzystania z biblioteki Marshal CLR. W tym przypadku C4996 jest błędem, a nie ostrzeżeniem. Ten błąd występuje, gdy używasz [`marshal_as`](../../dotnet/marshal-as.md) do konwersji między dwoma typami danych, które wymagają [ `marshal_context` klasy](../../dotnet/marshal-context-class.md). Możesz również otrzymać ten błąd, gdy biblioteka Marshal nie obsługuje konwersji. Aby uzyskać więcej informacji na temat biblioteki Marshaling, zobacz [Omówienie organizowania w języku C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Ten przykład generuje C4996, ponieważ biblioteka Marshal wymaga kontekstu do konwersji z `System::String` do `const char *` .

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>Przykład: funkcja przestarzała zdefiniowana przez użytkownika

Możesz użyć `deprecated` atrybutu w własnym kodzie, aby ostrzec wywołujących, gdy nie zaleca się już używania niektórych funkcji. W tym przykładzie C4996 jest generowana w dwóch miejscach: jeden dla wiersza, w którym zainstalowano przestarzałą funkcję, i jeden dla wiersza, w którym jest używana funkcja.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
