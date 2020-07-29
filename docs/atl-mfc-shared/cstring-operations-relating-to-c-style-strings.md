---
title: Operacje CString odnoszące się do ciągów w stylu C
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
ms.openlocfilehash: bbf483703b04c26c9462e4fe6adb08b614e440f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222046"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>Operacje CString odnoszące się do ciągów w stylu C

Obiekt [CString](../atl-mfc-shared/using-cstring.md) zawiera dane ciągu znaków. `CString`dziedziczy zestaw [metod i operatorów](../atl-mfc-shared/reference/cstringt-class.md) , które są zdefiniowane w szablonie klasy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) do pracy z danymi ciągu. ( `CString` jest to **`typedef`** specjalizacja `CStringT` do pracy z rodzajem danych znakowych obsługiwanych przez program `CString` ).

`CString`dane znakowe nie są przechowywane wewnętrznie jako ciąg w stylu C zakończony wartością null. Zamiast tego `CString` śledzi długość danych znakowych, dzięki czemu może bezpiecznie oglądać dane i wymagane miejsce.

`CString`akceptuje ciągi w stylu C i zapewnia sposoby dostępu do danych znakowych jako ciąg w stylu języka C. Ten temat zawiera następujące sekcje, które wyjaśniają, jak używać `CString` obiektu w taki sposób, jakby był ciągiem typu C zakończonym znakiem null.

- [Konwertowanie do ciągów zakończonych znakiem null w stylu języka C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Praca z funkcjami ciągu standardowej biblioteki wykonawczej](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Modyfikowanie zawartości CString bezpośrednio](#_core_modifying_cstring_contents_directly)

- [Używanie obiektów CString z funkcjami zmiennych argumentów](#_core_using_cstring_objects_with_variable_argument_functions)

- [Określanie parametrów formalnych CString](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>Używanie CString jako ciągu znaków zakończonych znakiem null w stylu C

Aby użyć `CString` obiektu jako ciągu w stylu C, rzutowanie obiektu na LPCTSTR. W poniższym przykładzie `CString` zwraca wskaźnik do ciągu języka C w stylu języka c++, który jest zakończony znakiem null. `strcpy`Funkcja umieszcza kopię ciągu w stylu C w zmiennej `myString` .

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Można użyć `CString` metod, na przykład, `SetAt` do modyfikacji pojedynczych znaków w obiekcie String. Jednak wskaźnik LPCTSTR jest tymczasowy i jest nieprawidłowy, gdy zostanie wprowadzona jakakolwiek zmiana `CString` . `CString`Może również wykroczyć zakres i być automatycznie usunięty. Zalecamy uzyskanie nowego LPCTSTRego wskaźnika `CString` obiektu za każdym razem, gdy jest on używany.

Czasami może być konieczne `CString` bezpośrednie modyfikowanie kopii danych. Użyj bardziej zabezpieczonej funkcji `strcpy_s` (lub Unicode/MBCS-Portable `_tcscpy_s` ), aby skopiować `CString` obiekt do oddzielnego buforu. Jest to miejsce, w którym można bezpiecznie zmodyfikować znaki, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Trzeci argument do `strcpy_s` (lub Unicode/MBCS-Portable `_tcscpy_s` ) ma postać `const wchar_t*` (Unicode) lub `const char*` (ANSI). Powyższy przykład przekazuje `CString` dla tego argumentu. Kompilator języka C++ automatycznie stosuje funkcję konwersji zdefiniowaną dla `CString` klasy, która konwertuje element `CString` na `LPCTSTR` . Możliwość definiowania operacji rzutowania z jednego typu na inny to jedna z najbardziej przydatnych funkcji języka C++.

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>Praca z funkcjami ciągu standardowej biblioteki wykonawczej

Powinno być możliwe znalezienie `CString` metody w celu wykonania dowolnej operacji na ciągach, dla których można rozważyć użycie standardowych funkcji ciągu biblioteki wykonawczej C, takich jak `strcmp` (lub Unicode/MBCS-Portable `_tcscmp` ).

Jeśli konieczne jest użycie funkcji ciągu czasu wykonywania języka C, można użyć technik opisanych w _core_using_cstring_as_a_c. 2D. style_null. 2D. terminated_string. Można skopiować `CString` obiekt do równoważnego buforu ciągu języka c, wykonać operacje na buforze, a następnie przypisać otrzymany ciąg stylu c z powrotem do `CString` obiektu.

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a>Modyfikowanie zawartości CString bezpośrednio

W większości sytuacji należy użyć `CString` funkcji składowych, aby zmodyfikować zawartość `CString` obiektu lub skonwertować `CString` ciąg znaków w stylu C.

Istnieją sytuacje, w których warto bezpośrednio modyfikować `CString` zawartość, na przykład podczas pracy z funkcjami systemu operacyjnego, które wymagają buforu znaków.

`GetBuffer`Metody i `ReleaseBuffer` oferują dostęp do wewnętrznego buforu znaków `CString` obiektu i pozwalają na ich modyfikowanie bezpośrednio. Poniższe kroki pokazują, jak używać tych funkcji do tego celu.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Aby użyć metody GetBuffer i ReleaseBuffer w celu uzyskania dostępu do wewnętrznego buforu znaków obiektu CString

1. Wywołaj `GetBuffer` dla `CString` obiektu i określ długość wymaganego buforu.

1. Użyj wskaźnika zwróconego przez, `GetBuffer` Aby pisać znaki bezpośrednio w `CString` obiekcie.

1. Wywołaj metodę `ReleaseBuffer` `CString` , aby zaktualizować wszystkie wewnętrzne `CString` Informacje o stanie, na przykład długość ciągu. Po zmodyfikowaniu zawartości `CString` obiektu należy wywołać `ReleaseBuffer` przed wywołaniem innych `CString` funkcji Członkowskich.

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a>Używanie obiektów CString z funkcjami zmiennych argumentów

Niektóre funkcje języka C przyjmują zmienną liczbę argumentów. Przykładem jest `printf_s` . Ze względu na sposób, w jaki jest zadeklarowany ten rodzaj funkcji, kompilator nie może sprawdzić typu argumentów i nie może określić, która operacja konwersji ma zostać wykonana dla każdego argumentu. W związku z tym należy użyć jawnego rzutowania typu podczas przekazywania `CString` obiektu do funkcji, która przyjmuje zmienną liczbę argumentów.

Aby użyć `CString` obiektu w funkcji argumentu zmiennej, należy jawnie rzutować `CString` na ciąg LPCTSTR, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a>Określanie parametrów formalnych CString

W przypadku większości funkcji, które wymagają argumentu ciągu, najlepszym rozwiązaniem jest określenie parametru formalnego w prototypie funkcji jako **`const`** wskaźnika do znaku ( `LPCTSTR` ) zamiast elementu `CString` . Gdy parametr formalny jest określony jako **`const`** wskaźnik do znaku, można przekazać wskaźnik do tablicy używanie TCHAR, ciągu literału [ `"hi there"` ] lub `CString` obiektu. `CString`Obiekt zostanie automatycznie przekonwertowany na LPCTSTR. W dowolnym miejscu możesz użyć LPCTSTR, można również użyć `CString` obiektu.

Można również określić parametr formalny jako odwołanie do ciągu stałego (czyli `const CString&` ), jeśli argument nie zostanie zmodyfikowany. Usuń **`const`** modyfikator, jeśli ciąg zostanie zmodyfikowany przez funkcję. Jeśli jest wymagana domyślna wartość null, zainicjuj ją w ciągu o wartości null [ `""` ], jak pokazano poniżej:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

W przypadku większości wyników funkcji można po prostu zwrócić `CString` obiekt według wartości.

## <a name="see-also"></a>Zobacz także

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Przekazywanie argumentu CString](../atl-mfc-shared/cstring-argument-passing.md)
