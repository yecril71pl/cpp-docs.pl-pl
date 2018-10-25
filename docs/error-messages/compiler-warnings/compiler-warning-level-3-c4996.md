---
title: Kompilator ostrzeżenie (poziom 3) C4996 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dff9f3c988e7ffdf8f15b5502bb0326e2692a128
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079041"
---
# <a name="compiler-warning-level-3-c4996"></a>Kompilator ostrzeżenie (poziom 3) C4996

Kompilator napotkał przestarzałe deklaracji. **To ostrzeżenie jest zawsze zamierzonego wiadomości od autora biblioteki lub plik nagłówkowy uwzględnione, że przestarzałe symboli nie należy używać bez zrozumienia konsekwencji.** Rzeczywiste komunikat ostrzegawczy jest określony przez modyfikator wycofywania lub atrybut w witrynie deklaracji.

Oto niektóre typowe komunikaty C4996, które są generowane przez Biblioteka uruchomieniowa C i standardową bibliotekę, ale nie stanowi wyczerpującej listy. Skorzystaj z łączy lub Czytaj dalej sposobów, aby rozwiązać ten problem, lub aby wyłączyć to ostrzeżenie.

- [Nazwa modelu POSIX dla tego elementu jest przestarzały. Zamiast tego należy użyć nazwy zgodność ISO C i C++: *nowa_nazwa*. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#posix-function-names)

- [Ta funkcja lub zmienna może być niebezpieczne. Należy rozważyć użycie *safe_version* zamiast tego. Aby wyłączyć wycofywania, użyj \_CRT\_bezpiecznego\_nie\_ostrzeżenia.  Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#unsafe-crt-library-functions)

- [' std::*nazwa_funkcji*::\_niezaznaczone\_Iteratory::\_Deprecate "wywołanie std::*nazwa_funkcji*z parametrami, które mogą być niebezpieczne — to wywołanie zależy obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne. Aby wyłączyć to ostrzeżenie, użyj -D_SCL_SECURE_NO_WARNINGS. Zobacz dokumentację na temat używania 'Sprawdzanych iteratorów' języka Visual C++](#unsafe-standard-library-functions)

- [Ta funkcja lub zmienna została zastąpiona nowsze funkcje biblioteki lub systemu operacyjnego. Należy rozważyć użycie *new_item* zamiast tego. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>Przyczyna

C4996 występuje, gdy kompilator napotka funkcji lub zmienna, która jest oznaczona jako [przestarzałe](../../cpp/deprecated-cpp.md) przy użyciu `__declspec(deprecated)` modyfikator, lub gdy spróbuje uzyskać dostęp do funkcji, elementu członkowskiego klasy lub typedef, który ma C ++ 14 [ \[ \[przestarzałe\] \] ](../../cpp/attributes.md) atrybutu. Możesz użyć `__declspec(deprecated)` modyfikator lub `[[deprecated]]` atrybutu samodzielnie biblioteki lub plików nagłówkowych, aby ostrzec klientów o zaniechanych funkcji, zmiennych, składowych lub definicje typów.

## <a name="remarks"></a>Uwagi

Wiele funkcji, funkcji składowych, template — funkcje i zmienne globalne w bibliotekach w programie Visual Studio, które są oznaczone jako *przestarzałe*. Te funkcje są przestarzałe, ponieważ może mieć inną nazwę preferowanego, mogą być niebezpieczne lub mieć wariant bardziej bezpieczne, lub mogą być nieaktualne. Komunikaty o zakończeniu obsługi wielu obejmować sugerowane zastępuje zaniechanej funkcji lub zmienna globalna.

Aby rozwiązać ten problem, zazwyczaj zalecamy zmienisz swój kod, aby zamiast tego użyj sugerowanego bezpieczniejsze lub zaktualizowane funkcje i zmienne globalne. Jeśli musisz używać istniejących funkcji lub zmienne powodów przenośność można wyłączyć to ostrzeżenie.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Aby wyłączyć ostrzeżenia bez rozwiązywania problemu

Ostrzeżenie dotyczące konkretnego wiersza kodu można wyłączyć za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma, `#pragma warning(suppress : 4996)`. Można również wyłączyć ostrzeżenia w pliku za pomocą pragmy ostrzeżenie `#pragma warning(disable : 4996)`.

Możesz wyłączyć to ostrzeżenie globalnie w kompilacji z wiersza polecenia przy użyciu **/wd4996** opcji wiersza polecenia.

Aby wyłączyć ostrzeżenia dla całego projektu w środowisku IDE programu Visual Studio:

- Otwórz **stron właściwości** okno dialogowe dla Twojego projektu. Aby uzyskać informacje dotyczące sposobu używania okna dialogowego strony właściwości, zobacz [stron właściwości](../../ide/property-pages-visual-cpp.md).
- Wybierz **właściwości konfiguracji**, **C/C++**, **zaawansowane** strony.
- Edytuj **Wyłącz określone ostrzeżenia** właściwości do dodania `4996`. Wybierz **OK** Aby zastosować zmiany.

Makra preprocesora umożliwia również wyłączyć niektórych określonych klas używane w bibliotekach ostrzeżeń dotyczących zakończenia obsługi. Te makra są opisane poniżej.

Aby zdefiniować makro preprocesora w programie Visual Studio:

- Otwórz **stron właściwości** okno dialogowe dla Twojego projektu. Aby uzyskać informacje dotyczące sposobu używania okna dialogowego strony właściwości, zobacz [stron właściwości](../../ide/property-pages-visual-cpp.md).
- Rozwiń **właściwości konfiguracji > C/C++ > preprocesora**.
- W **definicje preprocesora** właściwości, Dodaj nazwę makra. Wybierz **OK** Zapisz, a następnie ponownie skompiluj projekt.

Aby zdefiniować makro tylko w plikach określonego źródła, Dodaj wiersz takich jak `#define EXAMPLE_MACRO_NAME` przed każdego wiersza, który zawiera plik nagłówkowy.

## <a name="specific-c4996-messages"></a>Określone komunikaty C4996

Poniżej przedstawiono niektóre typowe źródła C4996 ostrzeżeń i błędów.

### <a name="posix-function-names"></a>POSIX — nazwy funkcji

**Nazwa modelu POSIX dla tego elementu jest przestarzały. Zamiast tego należy użyć nazwy zgodność ISO C i C++:** *nowa_nazwa*. **Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

Microsoft zmienił niektórych funkcji CRT, aby były zgodne z C99 C ++ 03 nazw i reguł zdefiniowanych w implementacji funkcja globalna POSIX. Tylko oryginalne nazwy POSIX są przestarzałe, nie same funkcje. W większości przypadków wiodącego podkreślenia dodano nazwę funkcji POSIX, aby utworzyć nazwę standardowego zgodność. Kompilator generuje ostrzeżenie o zakończeniu obsługi w oryginalnej nazwy funkcji, a także sugeruje nazwę preferowanego.

Aby rozwiązać ten problem, zazwyczaj zalecamy zmienisz swój kod, aby zamiast tego użyj nazwy funkcji sugerowanej. Jednak zaktualizowano nazwy są specyficzne dla firmy Microsoft. Jeśli musisz użyć istniejącej nazwy funkcji ze względów przenośność, można wyłączyć tych ostrzeżeń. Funkcje POSIX są nadal dostępne w bibliotece w obszarze oryginalne nazwy.

Aby wyłączyć ostrzeżeń dotyczących zakończenia obsługi dla tych funkcji, należy zdefiniować makro preprocesora  **\_CRT\_NONSTDC\_nie\_ostrzeżenia**. Możesz zdefiniować tego makra w wierszu polecenia, łącznie z opcją `/D_CRT_NONSTDC_NO_WARNINGS`.

### <a name="unsafe-crt-library-functions"></a>Niezabezpieczone funkcje biblioteki CRT

**Ta funkcja lub zmienna może być niebezpieczne. Należy rozważyć użycie** *safe_version* **zamiast tego. Aby wyłączyć wycofywania, użyj \_CRT\_bezpiecznego\_nie\_ostrzeżenia.  Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

Niektóre funkcje CRT i standardowej biblioteki języka C++ i funkcje globalne na rzecz bardziej bezpieczne wersje jest przestarzała firmy Microsoft. W większości przypadków zaniechanych funkcji umożliwiają unchecked odczytu lub zapisu do buforów, które może prowadzić do problemów z powodu poważnego naruszenia zabezpieczeń. Kompilator generuje ostrzeżenie o zakończeniu obsługi dla tych funkcji, a także sugeruje preferowana funkcja.

Aby rozwiązać ten problem, zalecane jest użycie funkcji lub zmienna *safe_version* zamiast tego. Upewnieniu się, że nie ma możliwości zastąpienia buforu lub overread wystąpić w kodzie, a nie można zmienić kod przyczyny przenoszenia, można wyłączyć to ostrzeżenie.

Aby wyłączyć ostrzeżeń dotyczących zakończenia obsługi dla tych funkcji w CRT, zdefiniuj  **\_CRT\_bezpiecznego\_nie\_ostrzeżenia**. Aby wyłączyć ostrzeżenia dotyczące przestarzałe zmiennych globalnych, zdefiniuj  **\_CRT\_bezpiecznego\_nie\_ostrzeżenia\_GLOBALS**. Aby uzyskać więcej informacji o tych przestarzałe funkcje i zmienne globalne, zobacz [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md) i [bezpieczne biblioteki: Standardowa biblioteka C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Niezabezpieczone funkcje biblioteki standardowej

__' std::__*nazwa_funkcji*__::\_niezaznaczone\_Iteratory::\_Deprecate "wywołanie std::__*nazwa_funkcji* **z parametrami, które mogą być niebezpieczne — to wywołanie zależy obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne. Aby wyłączyć to ostrzeżenie, użyj -D\_SCL\_bezpiecznego\_nie\_ostrzeżenia. Zobacz dokumentację na temat używania 'Sprawdzanych iteratorów' języka Visual C++**

To ostrzeżenie jest wyświetlane w kompilacjach debugowania, ponieważ niektóre funkcje szablonu standardowej biblioteki języka C++ sprawdza parametry pod kątem poprawności. W większości przypadków jest to, ponieważ nie ma wystarczającej ilości informacji znajduje się w funkcji w celu sprawdź granice kontenera lub Iteratory mogą być używane niepoprawnie za pomocą funkcji. To ostrzeżenie pomaga zidentyfikować te zastosowania funkcji, ponieważ mogą one być źródłem otworów powodu poważnego naruszenia zabezpieczeń w programach. Aby uzyskać więcej informacji, zobacz [Checked Iterators](../../standard-library/checked-iterators.md).

Na przykład, to ostrzeżenie jest wyświetlane w trybie debugowania w przypadku przekazania wskaźnika elementu do `std::copy` zamiast zwykłego tablicy. Aby rozwiązać ten problem, użyj tablicy odpowiednio zadeklarowane, więc sprawdza, czy zakresy tablicy i wykonaj sprawdzanie granic biblioteki.

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

Kilka algorytmami standardowej biblioteki zostały zaktualizowane, aby "podwójna zakresu" wersja w języku C ++ 14. Jeśli używasz wersji podwójną zakresu, drugi zakres zawiera konieczne sprawdzanie granic:

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

W przykładzie pokazano kilka sposobów więcej standardowej biblioteki mogą służyć do sprawdzania użycia iteratora i kiedy unchecked użycia może być niebezpieczne:

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

Jeśli sprawdzono, że Twój kod nie może mieć błąd w funkcji biblioteki standardowej, które mogą powodować to ostrzeżenie przepełnienie buforu, można wyłączyć to ostrzeżenie. Aby wyłączyć ostrzeżenia dla tych funkcji, należy zdefiniować  **\_SCL\_bezpiecznego\_nie\_ostrzeżenia**.

### <a name="checked-iterators-enabled"></a>Iteratory sprawdzane włączone

C4996 może również wystąpić, jeśli nie używasz iteratora sprawdzanego podczas kompilacji z `_ITERATOR_DEBUG_LEVEL` zdefiniowana jako 1 lub 2. Ustawiono na 2 domyślnie dla kompilacji w trybie debugowania, a 0 dla kompilacji detalicznej. Zobacz [Checked Iterators](../../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

### <a name="unsafe-mfc-or-atl-code"></a>Kod niebezpieczny MFC lub ATL

C4996 może również wystąpić, jeśli używasz funkcji biblioteki ATL i MFC, które zostały zaniechane ze względów bezpieczeństwa.

Aby rozwiązać ten problem, zdecydowanie zalecamy zmienisz swój kod, aby zamiast tego użyj zaktualizowanych funkcji.

Aby uzyskać informacje na temat pominąć te ostrzeżenia, zobacz [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Przestarzałe funkcje CRT i zmienne

**Ta funkcja lub zmienna została zastąpiona nowsze funkcje biblioteki lub systemu operacyjnego. Należy rozważyć użycie** *new_item* **zamiast tego. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

Niektóre funkcje i zmienne globalne są przestarzałe jako przestarzałe. Te funkcje i zmienne mogą zostać usunięte w przyszłej wersji biblioteki. Kompilator generuje ostrzeżenie o zakończeniu obsługi w przypadku tych elementów i sugeruje preferowana alternatywa.

Aby rozwiązać ten problem, zalecane jest zmiana kodu, aby użyć sugerowanych funkcji lub zmiennej.

Aby wyłączyć ostrzeżeń dotyczących zakończenia obsługi dla tych elementów, należy zdefiniować  **\_CRT\_OBSOLETE\_nie\_ostrzeżenia**. Aby uzyskać więcej informacji zobacz temat w dokumentacji zaniechanej funkcji lub zmienna.

### <a name="marshalling-errors-in-clr-code"></a>Kierowania błędów w kodzie CLR

C4996 może również wystąpić, gdy używasz Biblioteka dotycząca organizowania CLR. W tym przypadku C4996 jest błędem, a nie ostrzeżeniem. Ten błąd występuje, gdy używasz [marshal_as](../../dotnet/marshal-as.md) do konwersji między dwoma typami danych, które wymagają [marshal_context Class](../../dotnet/marshal-context-class.md). Ten błąd może również występować, gdy biblioteka dotycząca organizowania nie obsługuje konwersji. Aby uzyskać więcej informacji dotyczących biblioteki masrhaling, zobacz [Overview of Marshaling w C++](../../dotnet/overview-of-marshaling-in-cpp.md).

Ten przykład generuje C4996, ponieważ biblioteka dotycząca organizowania wymaga kontekstu, aby skonwertować z `System::String` do `const char *`.

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

## <a name="example-user-defined-deprecated-function"></a>Przykład: Zdefiniowane przez użytkownika funkcja przestarzałe

Atrybut przestarzałe we własnym kodzie umożliwia Ostrzegaj wywołań, gdy już nie zaleca się użycie niektórych funkcji. W tym przykładzie C4996 jest generowany dla wiersza, w którym zadeklarowano zaniechanej funkcji i dla wiersza, na którym jest używana funkcja.

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

__declspec(deprecated) void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
