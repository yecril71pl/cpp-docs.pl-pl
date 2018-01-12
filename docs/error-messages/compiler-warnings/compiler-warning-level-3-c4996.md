---
title: "Kompilatora (poziom 3) ostrzeżenie C4996 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4996
dev_langs: C++
helpviewer_keywords: C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e5a4797b4ac5fabc31d747682579c3b3ae6ce900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4996"></a>Kompilator C4996 ostrzegawcze (poziom 3)

Kompilator napotkano przestarzałe deklarację. **To ostrzeżenie jest zawsze zamierzonego komunikat z autorem biblioteki lub dołączony nagłówek pliku, że nie należy używać przestarzały symbolu bez zrozumienia konsekwencji tego działania.** Rzeczywiste komunikat ostrzegawczy jest określany przez modyfikator amortyzacja lub atrybutu w witrynie deklaracji. 

Oto niektóre typowe komunikaty C4996 wygenerowane przez biblioteki wykonawczej C i biblioteki standardowej, ale nie stanowi wyczerpującej listy. Skorzystaj z linków lub odczytywane na sposoby rozwiązania problemu lub wyłącz ostrzeżenia. 

- [Nazwa POSIX dla tego elementu jest przestarzały. Zamiast tego użyj nazwy zgodność ISO C i C++: *nowa_nazwa*. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#posix-function-names)

- [Tej funkcji lub zmienna może być niebezpieczne. Należy rozważyć użycie *safe_version* zamiast tego. Aby wyłączyć amortyzacja, należy użyć \_CRT\_bezpiecznego\_nr\_ostrzeżenia.  Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#unsafe-crt-library-functions)

- ["std::*nazwa_funkcji*::\_niezaznaczone\_Iteratory::\_Deprecate" wywołanie std::*nazwa_funkcji*z parametrami, które mogą być niebezpieczne — wywołanie polega na obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne. Aby wyłączyć to ostrzeżenie, użyj -D_SCL_SECURE_NO_WARNINGS. Dokumentacji na temat korzystania z programu Visual C++ 'Iteratory sprawdzane'](#unsafe-standard-library-functions)

- [Tej funkcji lub zmienna została zastąpiona nowszą funkcje biblioteki lub systemu operacyjnego. Należy rozważyć użycie *new_item* zamiast tego. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>Przyczyna

C4996 występuje, gdy kompilator napotka funkcji lub zmienna, która jest oznaczona jako [przestarzałe](../../cpp/deprecated-cpp.md) za pomocą `__declspec(deprecated)` modyfikator, lub usiłujące uzyskać dostęp do funkcji, element członkowski klasy lub element typedef, który ma C ++ 14 [ \[ \[przestarzałe\] \] ](../../cpp/attributes2.md) atrybutu. Można użyć `__declspec(deprecated)` modyfikator lub `[[deprecated]]` atrybutu samodzielnie w bibliotekach lub pliki nagłówkowe, aby ostrzec klientów o przestarzałych funkcji, zmiennych, elementów członkowskich lub definicje typów.

## <a name="remarks"></a>Uwagi

Wiele funkcji, funkcje Członkowskie szablonu funkcje i zmienne globalne w bibliotekach programu Visual Studio są oznaczone jako *przestarzałe*. Te funkcje są przestarzałe, ponieważ mogą mieć inną nazwę preferowanego, może być niebezpieczne lub mieć bardziej bezpieczne variant, lub mogą być nieaktualne. Wiele komunikatów amortyzacja obejmują sugerowane zastępuje funkcję przestarzałe lub zmiennej globalnej.

Aby rozwiązać ten problem, zwykle zaleca się zmienić swój kod, aby zamiast tego użyj sugerowane bezpieczniejsze lub zaktualizowane funkcje i zmienne globalne. Jeśli musisz używać istniejących funkcji lub zmienne przenośność ze względu na to ostrzeżenie można wyłączyć.

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>Aby wyłączyć ostrzeżenia bez rozwiązywania problemu

Ostrzeżenie dla określonego wiersza kodu można wyłączyć za pomocą [ostrzeżenie](../../preprocessor/warning.md) pragma, `#pragma warning(suppress : 4996)`. Można również wyłączyć ostrzeżenia w pliku za pomocą pragma ostrzeżenie `#pragma warning(disable : 4996)`.

Można wyłączyć ostrzeżenia globalnie w kompilacjach wiersza polecenia przy użyciu **/wd4996** opcji wiersza polecenia.

Aby wyłączyć ostrzeżenia dla całego projektu w środowisku IDE programu Visual Studio:

- Otwórz **strony właściwości** okna dialogowego dla projektu. Aby uzyskać informacje na temat sposobu użycia okna dialogowego strony właściwości, zobacz [strony właściwości](../../ide/property-pages-visual-cpp.md).
- Wybierz **właściwości konfiguracji**, **C/C++**, **zaawansowane** strony.
- Edytuj **Wyłącz określone ostrzeżenia** właściwości, aby dodać `4996`. Wybierz **OK** Aby zastosować zmiany.

Aby wyłączyć niektórych określonych klas ostrzeżenia dotyczące zaniechania używane w bibliotekach umożliwia także makra preprocesora. Poniżej opisano te makra.

Aby zdefiniować makro preprocesora w programie Visual Studio:

- Otwórz **strony właściwości** okna dialogowego dla projektu. Aby uzyskać informacje na temat sposobu użycia okna dialogowego strony właściwości, zobacz [strony właściwości](../../ide/property-pages-visual-cpp.md).
- Rozwiń węzeł **właściwości konfiguracji > C/C++ > preprocesora**.
- W **definicje preprocesora** właściwości, Dodaj nazwę makra. Wybierz **OK** Aby zapisać i ponownie skompiluj projekt.

Aby zdefiniować makro tylko w plikach określonego źródła, Dodaj wiersz na takich `#define EXAMPLE_MACRO_NAME` przed każdy wiersz, który zawiera plik nagłówka.

## <a name="specific-c4996-messages"></a>Określone komunikaty C4996

Poniżej przedstawiono niektóre typowe źródeł C4996 ostrzeżeń i błędów.

### <a name="posix-function-names"></a>Nazwy funkcji POSIX

**Nazwa POSIX dla tego elementu jest przestarzały. Zamiast tego użyj nazwy zgodność ISO C i C++:** *nowa_nazwa*. **Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

Microsoft zmienił niektóre funkcje POSIX w CRT odpowiadają C99 C ++ 03 nazw i reguł zdefiniowane w implementacji funkcji globalnej. Tylko oryginalnej nazwy POSIX są przestarzałe, nie same funkcje. W większości przypadków podkreśleniem początku został dodany do POSIX nazwę funkcji, aby utworzyć nazwę standardowego zgodność. Kompilator generuje ostrzeżenie oryginalnej nazwy funkcji i sugeruje preferowana nazwa.

Aby rozwiązać ten problem, zwykle zaleca się zmienić swój kod, aby zamiast tego użyj nazwy sugerowanych funkcji. Jednak zaktualizowany nazwy są specyficzne dla firmy Microsoft. Jeśli musisz użyć istniejącej nazwy funkcji przyczyn przenośność, można wyłączyć te ostrzeżenia. Funkcje POSIX są nadal dostępne w bibliotece w ich oryginalnych nazw.

Aby wyłączyć ostrzeżenia dotyczące zaniechania dla tych funkcji, należy zdefiniować makro preprocesora  **\_CRT\_NONSTDC\_nr\_ostrzeżenia**. To makro w wierszu polecenia można zdefiniować przy tym opcję `/D_CRT_NONSTDC_NO_WARNINGS`.


### <a name="unsafe-crt-library-functions"></a>Niebezpieczne funkcje biblioteki CRT

 **Tej funkcji lub zmienna może być niebezpieczne. Należy rozważyć użycie** *safe_version* **zamiast tego. Aby wyłączyć amortyzacja, należy użyć \_CRT\_bezpiecznego\_nr\_ostrzeżenia.  Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

 Microsoft jest przestarzała, niektóre funkcje CRT i standardowej biblioteki C++ i funkcje globalne na rzecz wersji bardziej bezpieczne. W większości przypadków przestarzałe funkcje Zezwalaj niezaznaczone odczytu lub zapisu do buforów, które może prowadzić do problemów zabezpieczenia. Kompilator generuje ostrzeżenie dla tych funkcji i sugeruje preferowana funkcja.

 Aby rozwiązać ten problem, zalecane jest użycie funkcji lub zmienna *safe_version* zamiast tego. Jeśli po sprawdzeniu, czy nie jest możliwe w dla Zastąp buforu lub overread w kodzie i nie można zmienić kod przyczyny przenoszenia, można wyłączyć to ostrzeżenie.
 
 Aby wyłączyć ostrzeżenia dotyczące zaniechania dla tych funkcji w CRT, zdefiniuj  **\_CRT\_bezpiecznego\_nr\_ostrzeżenia**. Aby wyłączyć ostrzeżenia o przestarzałe zmienne globalne, zdefiniuj  **\_CRT\_bezpiecznego\_nr\_ostrzeżenia\_GLOBALS**. Aby uzyskać więcej informacji na temat tych przestarzałe funkcje i zmienne globalne, zobacz [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md) i [bezpieczne biblioteki: Standardowa biblioteka C++](../../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="unsafe-standard-library-functions"></a>Niebezpieczne funkcje biblioteki standardowej

__"std::__*nazwa_funkcji*__::\_niezaznaczone\_Iteratory::\_Deprecate" wywołanie std::__*nazwa_funkcji* **z parametrami, które mogą być niebezpieczne — to wywołanie opiera się na obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne. Aby wyłączyć to ostrzeżenie, użyj -D\_SCL\_bezpiecznego\_nr\_ostrzeżenia. Dokumentacji na temat korzystania z programu Visual C++ 'Iteratory sprawdzane'**

To ostrzeżenie jest wyświetlane w kompilacjach debugowania, ponieważ niektóre funkcje szablonu standardowa biblioteka C++ sprawdza poprawność parametrów. W większości przypadków jest to ponieważ nie ma wystarczającej ilości informacji jest dostępna dla funkcji w celu sprawdzenia granice kontenera lub ponieważ Iteratory mogą niepoprawnie użyte przy użyciu funkcji. To ostrzeżenie pomaga zidentyfikować te zastosowań funkcji, ponieważ mogą one być źródłem luk w zabezpieczeniach poważne w programie. Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../../standard-library/checked-iterators.md).

Na przykład to ostrzeżenie jest wyświetlane w trybie debugowania w przypadku przekazania wskaźnik elementu `std::copy` zamiast zwykłego tablicy. Aby rozwiązać ten problem, użyj tablicy odpowiednio zadeklarowane, sprawdza, czy zakresy tablicy i wykonaj sprawdzanie granic biblioteki.

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

Wiele algorytmów standardowa biblioteka zostały zaktualizowane w celu zapewnienia wersje "podwójną zakresu" C ++ 14. Jeśli używasz wersji podwójną zakresu drugiego zakresu udostępnia niezbędne sprawdzanie granic:

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

W tym przykładzie pokazano kilka sposobów więcej biblioteki standardowej może służyć do sprawdzania użycia iteratora i po usunięciu zaznaczenia użycia może być niebezpieczne:

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

Jeśli po sprawdzeniu, czy kod nie może mieć błąd w funkcji biblioteki standardowej wyzwalających to ostrzeżenie przepełnienie buforu, możesz wyłączyć to ostrzeżenie. Aby wyłączyć ostrzeżenia dla tych funkcji, należy zdefiniować  **\_SCL\_bezpiecznego\_nr\_ostrzeżenia**.

### <a name="checked-iterators-enabled"></a>Zaznaczone Iteratory włączone

C4996 może również wystąpić, jeśli nie należy używać zaznaczone iteratora podczas kompilowania przy użyciu `_ITERATOR_DEBUG_LEVEL` zdefiniowany jako 1 lub 2. Ustawiono 2 domyślne dla kompilacji do trybu debugowania i 0 dla kompilacji sprzedaży detalicznej. Zobacz [zaznaczone Iteratory](../../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.

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

### <a name="unsafe-mfc-or-atl-code"></a>Kod niezabezpieczony MFC lub ATL

C4996 może również wystąpić, jeśli używasz MFC lub ATL funkcji, które były przestarzałe ze względów bezpieczeństwa.

Aby rozwiązać ten problem, zdecydowanie zaleca się zmienić swój kod, aby zamiast tego użyj funkcji zaktualizowane.

Aby uzyskać informacje dotyczące pominąć te ostrzeżenia, zobacz [_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings).

### <a name="obsolete-crt-functions-and-variables"></a>Przestarzałe funkcje CRT i zmienne

**Tej funkcji lub zmienna została zastąpiona nowszą funkcje biblioteki lub systemu operacyjnego. Należy rozważyć użycie** *new_item* **zamiast tego. Zobacz Pomoc online, aby uzyskać szczegółowe informacje.**

Niektóre funkcje i zmienne globalne są używane jako przestarzałe. Te funkcje i zmienne mogą zostać usunięte w przyszłej wersji biblioteki. Kompilator generuje ostrzeżenie dla tych elementów i sugeruje, preferowany alternatywnej.

Aby rozwiązać ten problem, zaleca się zmienić swój kod, aby użyć sugerowanych funkcji lub zmiennej.

Aby wyłączyć ostrzeżenia dotyczące zaniechania dla tych elementów, zdefiniuj  **\_CRT\_PRZESTARZAŁE\_nr\_ostrzeżenia**. Aby uzyskać więcej informacji zobacz dokumentację przestarzałych funkcji lub zmienna.

### <a name="marshalling-errors-in-clr-code"></a>Kierowanie błędów w kodzie CLR

C4996 może również wystąpić, gdy używasz biblioteki marshalingu CLR. W tym przypadku C4996 jest błędem, a nie ostrzeżeniem. Ten błąd występuje, gdy używasz [marshal_as —](../../dotnet/marshal-as.md) do konwersji między typami dwóch danych, które wymagają [marshal_context — klasa](../../dotnet/marshal-context-class.md). Ten błąd może również odbierać, gdy biblioteka organizowania nie obsługuje konwersji. Aby uzyskać więcej informacji na temat biblioteki marshalingu, zobacz [omówienie z Marshalingu w języku C++](../../dotnet/overview-of-marshaling-in-cpp.md).

W tym przykładzie generuje C4996, ponieważ biblioteka organizowania wymaga kontekstu do przekonwertowania z `System::String` do `const char *`.

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

Atrybut przestarzałe w swoim własnym kodem służy do wywoływania Ostrzegaj nie zaleca się użycie niektórych funkcji. W tym przykładzie C4996 jest generowany dla wiersza, w którym zadeklarowano przestarzałych funkcji, a dla wiersza, w którym jest używana funkcja.

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
