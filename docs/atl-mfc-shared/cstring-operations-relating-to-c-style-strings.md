---
title: CString — operacje odnoszące się do ciągów stylu C
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
ms.openlocfilehash: 406a934d3691c7787085cc319770074ac2ee5926
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317948"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>CString — operacje odnoszące się do ciągów stylu C

Obiekt [CString](../atl-mfc-shared/using-cstring.md) zawiera dane ciągu znaków. `CString`dziedziczy zestaw [metod i operatorów,](../atl-mfc-shared/reference/cstringt-class.md) które są zdefiniowane w szablonie klasy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) do pracy z danymi ciągu. (`CString` jest **typedef,** `CStringT` który specjalizuje się do pracy `CString` z rodzaju danych znaków, który obsługuje.)

`CString`nie przechowuje danych znaków wewnętrznie jako ciąg zakończony zerem w stylu C. Zamiast tego `CString` śledzi długość danych znaków, dzięki czemu można bezpieczniej obserwować dane i miejsce, które wymaga.

`CString`akceptuje ciągi w stylu C i udostępnia sposoby dostępu do danych znaków jako ciągu w stylu C. Ten temat zawiera następujące sekcje, które `CString` wyjaśniają, jak używać obiektu tak, jakby był ciągiem zakończonym zerem w stylu C.

- [Konwertowanie ciągów zakończonych zerem w stylu C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Praca ze standardowymi funkcjami ciągu biblioteki w czasie wykonywania](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Bezpośrednie modyfikowanie zawartości CString](#_core_modifying_cstring_contents_directly)

- [Używanie obiektów CString z funkcjami argumentów zmiennych](#_core_using_cstring_objects_with_variable_argument_functions)

- [Określanie parametrów formalnych CString](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>Używanie CString jako ciągu zakończonego w stylu C

Aby użyć `CString` obiektu jako ciągu w stylu C, należy rzutować obiekt na LPCTSTR. W poniższym przykładzie `CString` zwraca wskaźnik do ciągu zakończonego tylko do odczytu c. Funkcja `strcpy` umieszcza kopię ciągu w stylu C `myString`w zmiennej .

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Można użyć `CString` metod, na `SetAt`przykład, aby zmodyfikować poszczególne znaki w obiekcie ciągu. Jednak wskaźnik LPCTSTR jest tymczasowy i staje się `CString`nieprawidłowy, gdy wprowadzana jest jakakolwiek zmiana . Może `CString` również wyjść poza zakres i zostać automatycznie usunięty. Zaleca się, aby uzyskać świeży wskaźnik `CString` LPCTSTR obiektu za każdym razem, gdy używasz jednego.

Czasami może wymagać `CString` kopii danych do bezpośredniej modyfikacji. Użyj bardziej zabezpieczonej funkcji `strcpy_s` (lub Unicode/MBCS-portable), `_tcscpy_s`aby skopiować `CString` obiekt do oddzielnego buforu. W tym miejscu znaki mogą być bezpiecznie modyfikowane, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Trzeci argument `strcpy_s` do (lub Unicode/MBCS-portable) `_tcscpy_s`jest `const wchar_t*` (Unicode) `const char*` lub (ANSI). Powyższy przykład `CString` przekazuje dla tego argumentu. Kompilator C++ automatycznie stosuje funkcję konwersji `CString` zdefiniowaną dla `CString` klasy `LPCTSTR`konwertowane na . Możliwość definiowania operacji rzutowania z jednego typu do drugiego jest jedną z najbardziej przydatnych funkcji języka C++.

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>Praca ze standardowymi funkcjami ciągu biblioteki w czasie wykonywania

Można znaleźć `CString` metodę wykonywania dowolnej operacji ciągu, dla której można rozważyć użycie standardowych funkcji ciągu `strcmp` biblioteki w czasie wykonywania `_tcscmp`C, takich jak (lub Unicode/MBCS-portable).

Jeśli należy użyć funkcji ciągu wykonywania języka C, można użyć technik opisanych w _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Obiekt można `CString` skopiować do buforu ciągów w stylu C, wykonać operacje w buforze, a `CString` następnie przypisać wynikowy ciąg w stylu C z powrotem do obiektu.

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a>Bezpośrednie modyfikowanie zawartości cstring

W większości sytuacji należy `CString` użyć funkcji członkowskich, `CString` aby zmodyfikować `CString` zawartość obiektu lub przekonwertować ciąg znaków w stylu C.

Istnieją sytuacje, w których ma sens `CString` bezpośrednie modyfikowanie zawartości, na przykład podczas pracy z funkcjami systemu operacyjnego, które wymagają buforu znaków.

Metody `GetBuffer` `ReleaseBuffer` i oferują dostęp do wewnętrznego `CString` buforu znaków obiektu i umożliwiają jego bezpośrednią modyfikację. Poniższe kroki pokazują, jak korzystać z tych funkcji w tym celu.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Aby użyć GetBuffer i ReleaseBuffer, aby uzyskać dostęp do wewnętrznego buforu znaków obiektu CString

1. Wywołaj `GetBuffer` `CString` obiekt i określ długość buforu, którego potrzebujesz.

1. Użyj wskaźnika `GetBuffer` zwróconego przez do `CString` zapisu znaków bezpośrednio do obiektu.

1. Wywołanie `ReleaseBuffer` `CString` obiektu, aby zaktualizować `CString` wszystkie informacje o stanie wewnętrznym, na przykład długość ciągu. Po zmodyfikowaniu zawartości `CString` obiektu bezpośrednio, należy `ReleaseBuffer` wywołać przed `CString` wywołaniem innych funkcji członkowskich.

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a>Używanie obiektów CString z funkcjami argumentu zmiennego

Niektóre funkcje C przyjmują zmienną liczbę argumentów. Godnym uwagi `printf_s`przykładem jest . Ze względu na sposób tego rodzaju funkcji jest zadeklarowany, kompilator nie może być pewien typu argumentów i nie można określić, która operacja konwersji do wykonania na każdym argurze. W związku z tym jest niezbędne, aby użyć `CString` jawnego typu rzutowania podczas przekazywania obiektu do funkcji, która przyjmuje zmienną liczbę argumentów.

Aby użyć `CString` obiektu w funkcji argumentu zmiennej, jawnie rzutuj ciąg `CString` LPCTSTR, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a>Określanie parametrów formalnych CString

W przypadku większości funkcji, które wymagają argumentu ciągu, najlepiej jest określić parametr formalny w prototypie funkcji jako `const` wskaźnik do znaku (`LPCTSTR`) zamiast . `CString` Gdy parametr formalny jest `const` określony jako wskaźnik do znaku, można przekazać wskaźnik do tablicy TCHAR, ciąg literału [`"hi there"`], lub `CString` obiekt. Obiekt `CString` zostanie automatycznie przekonwertowany na LPCTSTR. W dowolnym miejscu można użyć LPCTSTR, `CString` można również użyć obiektu.

Można również określić parametr formalny jako odwołanie `const CString&`do ciągu stałego (czyli ), jeśli argument nie zostanie zmodyfikowany. Upuść **const** modyfikator, jeśli ciąg zostanie zmodyfikowany przez funkcję. Jeśli żądana jest domyślna wartość null, zainicjuj ją do ciągu zerowego [`""`], jak pokazano poniżej:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

Dla większości wyników funkcji można `CString` po prostu zwrócić obiekt według wartości.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString — przekazywanie argumentów](../atl-mfc-shared/cstring-argument-passing.md)
