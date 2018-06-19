---
title: Cstring — operacji odnoszących się do ciągów w stylu języka C | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 7d0683f82204b11d06b1952913d4dbdb1e4a468d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361817"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>Cstring — operacji odnoszących się do ciągów w stylu języka C
A [cstring —](../atl-mfc-shared/using-cstring.md) obiekt zawiera dane ciągu znaków. `CString` dziedziczy zbiór [metody i operatory](../atl-mfc-shared/reference/cstringt-class.md) które zostały zdefiniowane w szablonie klasy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) do pracy z danych ciągu. (`CString` jest `typedef` który specjalizuje się `CStringT` do pracy z typu danych znakowych który `CString` obsługuje.)  
  
 `CString` nie przechowuje danych znakowych wewnętrznie jako ciąg znaków zakończony znakiem null stylu języka C. Zamiast tego `CString` śledzi długość danych znakowych, dzięki czemu można bardziej bezpieczny sposób oglądać, danych i miejsca wymaga.  
  
 `CString` Zaakceptuj ciągów w stylu języka C, a dostępnych metod dostępu do danych znakowych jako ciąg w stylu języka C. Ten temat zawiera następujące sekcje, które opisano sposób użycia `CString` obiekt tak, jakby była zerem ciągu stylu języka C.  
  
- [Konwertowanie na ciągi zakończone wartością null w stylu języka C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
- [Praca z funkcjami ciąg standardowej biblioteki wykonawczej](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
- [Bezpośrednie modyfikowanie cstring — zawartość](#_core_modifying_cstring_contents_directly)  
  
- [Funkcje zmiennych argumentów przy użyciu cstring — obiekty](#_core_using_cstring_objects_with_variable_argument_functions)  
  
- [Określanie parametrów formalnych cstring —](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> Przy użyciu obiektu CString jako ciąg znaków zakończony znakiem Null stylu języka C  
 Aby użyć `CString` obiekt jako ciąg w stylu języka C, rzutowanie tego obiektu na `LPCTSTR`. W poniższym przykładzie `CString` zwraca wskaźnik do tylko do odczytu stylu języka C zerem ciągu. `strcpy` Funkcja umieszcza kopię ciągu stylu języka C w zmiennej `myString`.  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);
```  
  
 Można użyć `CString` metod, na przykład `SetAt`, aby zmodyfikować poszczególnych znaków z obiektem ciągu. Jednak `LPCTSTR` wskaźnika są tymczasowe i staje się nieprawidłowy, gdy dokonania zmian `CString`. `CString` Można również znaleźć poza zakresem i są automatycznie usuwane. Firma Microsoft zaleca, aby otrzymywały świeża `LPCTSTR` wskaźnik `CString` obiekt zawsze używać jednego.  
  
 Czasami może wymagać kopię `CString` danych można zmodyfikować bezpośrednio. Funkcja więcej zabezpieczonych `strcpy_s` (lub Unicode/MBCS — komputer przenośny `_tcscpy_s`) do skopiowania `CString` obiektu do oddzielnych buforu. Jest to gdzie znaki mogą być bezpiecznie modyfikowane, jak pokazano na poniższym przykładzie.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  Trzeci argument `strcpy_s` (lub Unicode/MBCS — komputer przenośny `_tcscpy_s`) albo `const wchar_t*` (Unicode) lub `const char*` (ANSI). Przykład powyżej przekazuje `CString` dla tego argumentu. Kompilator języka C++ automatycznie stosuje zdefiniowany dla funkcji konwersji `CString` klasy, który konwertuje `CString` do `LPCTSTR`. Możliwość definiowania operacji rzutowania z typu jest jednym z najbardziej przydatnych funkcji języka C++.  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Praca z funkcjami ciąg standardowej biblioteki wykonawczej  
 Można znaleźć `CString` metodę, aby wykonać żadnej operacji ciągu, dla którego należy rozważyć przy użyciu standardowych funkcji ciąg biblioteki wykonawczej języka C, takich jak `strcmp` (lub Unicode/MBCS — komputer przenośny `_tcscmp`).  
  
 Jeśli należy użyć funkcji ciągu środowiska wykonawczego języka C, możesz użyć metod opisanych w _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Możesz skopiować `CString` object równoważne buforu ciągu w stylu języka C, wykonaj operacje na buforu, a następnie przypisz wynikowy ciąg w stylu języka C z powrotem do `CString` obiektu.  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> Bezpośrednie modyfikowanie cstring — zawartość  
 W większości sytuacji należy użyć `CString` funkcji elementów członkowskich, aby zmodyfikować zawartość `CString` obiektu lub przekonwertować `CString` na ciąg znaków w stylu języka C.  
  
 Istnieje kilka sytuacji, w których warto bezpośrednio modyfikować `CString` zawartości, na przykład podczas pracy z funkcji systemu operacyjnego, które wymagają buforu znaków.  
  
 `GetBuffer` i `ReleaseBuffer` metody oferują dostęp do buforu wewnętrznego znak z `CString` obiektu i można go bezpośrednio modyfikować. Poniższe kroki przedstawiają sposób korzystania z tych funkcji w tym celu.  
  
#### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Na potrzeby dostępu buforu wewnętrznego znak obiektu cstring — GetBuffer i ReleaseBuffer  
  
1.  Wywołanie `GetBuffer` dla `CString` obiektu i określ długość buforu wymagane.  
  
2.  Za pomocą wskaźnika zwrócony przez `GetBuffer` zapisu znaków bezpośrednio do `CString` obiektu.  
  
3.  Wywołanie `ReleaseBuffer` dla `CString` aktualizację wszystkich wewnętrznego obiektu `CString` stanu informacje, na przykład długość ciągu. Po zmodyfikowaniu zawartość `CString` obiekt bezpośrednio, należy wywołać `ReleaseBuffer` przed wywołaniem innych `CString` funkcji elementów członkowskich.  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> Funkcje zmiennych argumentów przy użyciu cstring — obiekty  
 Niektóre funkcje C pobierać zmienną liczbę argumentów. Przykładem jest `printf_s`. Ze względu na sposób tego rodzaju funkcji jest zadeklarowana kompilator nie Pamiętaj typu argumentów i nie można ustalić konwersji operację wykonywaną na każdy argument. Dlatego jest ważne, że używasz jawnego typu rzutowania podczas przekazywania `CString` obiektu do funkcji, która przyjmuje zmienną liczbę argumentów.  
  
 Aby użyć `CString` obiektu w funkcji zmiennych argumentów jawnego rzutowania `CString` do `LPCTSTR` ciąg znaków, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> Określanie parametrów formalnych cstring —  
 Dla większości funkcji wymagających argument ciągu, najlepiej określić parametrów formalnych w prototypu funkcji jako `const` wskaźnik do znaku (`LPCTSTR`) zamiast `CString`. Gdy formalny parametr jest określony jako `const` wskaźnik do znaku, można przekazać wskaźnika do `TCHAR` tablicy literałem [`"hi there"`], lub `CString` obiektu. `CString` Obiektu zostaną automatycznie przekonwertowane na `LPCTSTR`. Miejsce można użyć `LPCTSTR`, można również użyć `CString` obiektu.  
  
 Można również określić parametr formalny jako odwołanie stałym ciągiem (czyli `const CString&`), jeśli argument nie zostaną zmodyfikowane. Upuść `const` modyfikator, jeśli ciąg zostanie zmodyfikowana przez funkcję. W razie potrzeby domyślne wartości null zainicjować go na ciąg null [`""`], jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 Dla większości funkcji wyniki, możesz po prostu powrócić `CString` obiektu przez wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString — przekazywanie argumentów](../atl-mfc-shared/cstring-argument-passing.md)

