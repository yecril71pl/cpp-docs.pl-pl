---
title: Cstring — operacje odnoszące się do ciągów stylu C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a2567182f0e2622a72ceb9b98988c4d122a3561
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860566"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>Cstring — operacje odnoszące się do ciągów stylu C

A [CString](../atl-mfc-shared/using-cstring.md) obiekt zawiera dane ciągu znaków. `CString` dziedziczy zestaw [metody i operatory](../atl-mfc-shared/reference/cstringt-class.md) , są zdefiniowane w szablonie klasy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) do pracy z danymi w ciągu. (`CString` jest **typedef** który specjalizuje się `CStringT` do pracy z typu danych znakowych, `CString` obsługuje.)

`CString` nie przechowuje danych znakowych wewnętrznie jako ciąg stylu C zakończony znakiem null. Zamiast tego `CString` śledzi długość danych znakowych, dzięki czemu można bardziej bezpieczne oglądać, dane i miejsce wymagane.

`CString` Zaakceptuj ciągi stylu C, zapewniając metody dostępu do danych znakowych jako ciąg stylu C. Ten temat zawiera następujące sekcje, które wyjaśniają jak używać `CString` obiektu tak, jakby był to ciąg stylu C zakończony znakiem null.

- [Konwertowanie na ciągi znaków zakończony znakiem null w stylu języka C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Praca z funkcjami ciąg standardowej biblioteki wykonawczej](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Bezpośrednie modyfikowanie zawartości CString](#_core_modifying_cstring_contents_directly)

- [Funkcje zmiennych argumentów za pomocą cstring — obiekty](#_core_using_cstring_objects_with_variable_argument_functions)

- [Określanie parametrów formalnych CString](#_core_specifying_cstring_formal_parameters)

##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> Użycie CString jako ciąg stylu C zakończony znakiem Null

Aby użyć `CString` obiektu jako ciąg stylu C, wykonaj rzutowanie obiektu LPCTSTR. W poniższym przykładzie `CString` zwraca wskaźnik do tylko do odczytu stylu C zakończony zerem ciągu. `strcpy` Funkcja umieszcza kopię ciąg stylu C w zmiennej `myString`.

```
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);
```

Możesz użyć `CString` metody, na przykład `SetAt`, aby zmodyfikować pojedynczych znaków w obiekcie string. Jednak wskaźnik LPCTSTR jest tymczasowe i staje się nieprawidłowy, gdy dokonania zmian `CString`. `CString` Można również wykraczają poza zakres i automatycznie usunięte. Firma Microsoft zaleca uzyskanie świeże wskaźnika LPCTSTR `CString` obiektu każdym razem, gdy używasz jednego.

Czasami może wymagać kopię `CString` dane, aby modyfikować bezpośrednio. Użyj funkcji bezpieczniejszy `strcpy_s` (lub Unicode/MBCS-przenośna `_tcscpy_s`) do skopiowania `CString` obiektu do oddzielnych buforu. To jest, których znaków można bezpiecznie modyfikować, jak pokazano na poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Trzeci argument `strcpy_s` (lub Unicode/MBCS-przenośna `_tcscpy_s`) jest `const wchar_t*` (Unicode) lub `const char*` (ANSI). Przykład powyżej przebiegów `CString` dla tego argumentu. Kompilator języka C++ automatycznie stosuje funkcję konwersji zdefiniowane dla `CString` klasy, która konwertuje `CString` do `LPCTSTR`. Możliwość definiowania operacji rzutowania z jednego typu jest jednym z najbardziej przydatnych funkcjach języka c++.

##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Praca z funkcjami ciąg standardowej biblioteki wykonawczej

Powinno być możliwe znaleźć `CString` metody, które można wykonać operacji dowolnego ciągu, dla których warto rozważyć przy użyciu standardowych funkcji ciągu biblioteki wykonawczej C, takich jak `strcmp` (lub Unicode/MBCS-przenośna `_tcscmp`).

Jeśli musisz użyć funkcji ciągu środowiska wykonawczego języka C, można użyć metod opisanych w _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Możesz skopiować `CString` obiektów równoważnych buforze ciąg stylu C, wykonywać operacje na buforu, a następnie przypisz wynikowy ciąg stylu C z powrotem do `CString` obiektu.

##  <a name="_core_modifying_cstring_contents_directly"></a> Bezpośrednie modyfikowanie zawartości CString

W większości przypadków należy używać `CString` funkcji elementów członkowskich do modyfikowania zawartości `CString` obiektu lub przekonwertować `CString` na ciąg znaków w stylu języka C.

Istnieją sytuacje, gdzie sens bezpośrednio modyfikować `CString` zawartości, na przykład podczas pracy z funkcjami systemu operacyjnego, które wymagają buforu znaków.

`GetBuffer` i `ReleaseBuffer` metody oferują dostęp do buforu wewnętrznego znaków, z `CString` obiektu i można go bezpośrednio modyfikować. Poniższe kroki pokazują sposób używania tych funkcji, w tym celu.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Na potrzeby dostępu do buforu wewnętrznego znaku obiektu CString getbuffer — i ReleaseBuffer

1. Wywołaj `GetBuffer` dla `CString` obiektu, a także określić długość buforu, potrzebujesz.

1. Użyj wskaźnika zwrócony przez `GetBuffer` do zapisu znaków bezpośrednio do `CString` obiektu.

1. Wywołaj `ReleaseBuffer` dla `CString` obiektu do zaktualizowania wszystkich wewnętrznych `CString` stanu informacji, na przykład długość ciągu. Po zmodyfikowaniu zawartość `CString` obiektu bezpośrednio, należy wywołać `ReleaseBuffer` przed wywołaniem innych `CString` funkcji elementów członkowskich.

##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> Funkcje zmiennych argumentów za pomocą cstring — obiekty

Niektóre funkcje C przyjmują zmienną liczbę argumentów. Przykład istotne jest `printf_s`. Ze względu na sposób, w jaki ten rodzaj funkcji jest zadeklarowana kompilator nie może mieć pewności, jaka typy argumentów i nie może określić, które operację konwersji do wykonania na każdy argument. Dlatego jest istotne, że używasz typu jawnego rzutowania przy przekazywaniu `CString` obiektu do funkcji, która przyjmuje zmienną liczbę argumentów.

Aby użyć `CString` obiektu w funkcji zmiennych argumentów, jawnie rzutowane `CString` LPCTSTR ciąg, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

##  <a name="_core_specifying_cstring_formal_parameters"></a> Określanie parametrów formalnych CString

Dla większości funkcji wymagających argument ciągu jest najlepsze do określania parametrów formalnych w prototypu funkcji jako `const` wskaźnik do znaku (`LPCTSTR`) zamiast `CString`. Gdy parametr formalny jest określony jako `const` wskaźnik do znaku, można przekazać albo wskaźnika do tablicy TCHAR, ciąg literału [`"hi there"`], czy też `CString` obiektu. `CString` Obiektu zostaną automatycznie przekonwertowane na LPCTSTR. Każde miejsce, można użyć LPCTSTR, można również użyć `CString` obiektu.

Można również określić parametr formalny jako odwołanie stałym ciągiem (czyli `const CString&`) Jeśli argument nie zostaną zmodyfikowane. Upuść **const** modyfikator, jeśli ciąg zostanie zmodyfikowana przez funkcję. Jeśli pożądane jest domyślna wartość null, zainicjuj ją na pusty ciąg [`""`], jak pokazano poniżej:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

Dla większości wyników funkcji, można po prostu zwrócenia `CString` obiekt przez wartość.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString — przekazywanie argumentów](../atl-mfc-shared/cstring-argument-passing.md)
