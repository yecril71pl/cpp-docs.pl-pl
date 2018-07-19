---
title: Operacje na obiekcie CString podstawowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccda8d6a1abd51f3463630435a14096edc30439d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879923"
---
# <a name="basic-cstring-operations"></a>Operacje na obiekcie CString podstawowe
W tym temacie opisano następujące podstawowe [CString](../atl-mfc-shared/reference/cstringt-class.md) operacje:  
  
- [Tworzenie obiektów CString z standard C literałów ciągów.](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [Uzyskiwanie dostępu do poszczególnych znaków CString](#_core_accessing_individual_characters_in_a_cstring)  
  
- [Łączenie dwóch cstring — obiekty](#_core_concatenating_two_cstring_objects)  
  
- [Porównywanie cstring — obiekty](#_core_comparing_cstring_objects)  
  
- [Konwersja z cstring — obiekty](#_core_converting_cstring_objects)  
  
 `Class CString` jest oparty na szablonie klasy [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md). `CString` jest **typedef** z `CStringT`. Bardziej dokładnie `CString` jest **typedef** z *jawna specjalizacja* z `CStringT`, która jest typowym sposobem zdefiniowania klasy przy użyciu szablonu klasy. Podobnie zdefiniowanych klas są `CStringA` i `CStringW`.  
  
 `CString`, `CStringA`, i `CStringW` są zdefiniowane w pliku atlstr.h. `CStringT` jest zdefiniowany w cstringt.h.  
  
 `CString`, `CStringA`, i `CStringW` uzyskać każdy zestaw metod i operatory zdefiniowane przez `CStringT` do użycia z usługą danych ciągu, które obsługują. Niektóre metody zduplikowany, a w niektórych przypadkach pozwoliło usług ciągu biblioteki wykonawczej C.  
  
 Uwaga: `CString` jest klasą natywnych. Dla klasy ciągu, która jest przeznaczona do użytku w języku C + +/ CLI zarządzanego projektu, użyj `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Tworzenie obiektów CString z ciągami tekstowymi Standard C  
 Można przypisać stylu C ciągami tekstowymi `CString` tak samo jak można przypisać jedną `CString` obiektu do drugiego.  
  
-   Przypisz wartość literału ciągu języka C do `CString` obiektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   Przypisz wartość jednego `CString` do innego `CString` obiektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     Zawartość `CString` obiektu są kopiowane, gdy dla jednego `CString` obiekt jest przypisany do innego. W związku z tym dwa ciągi znaków, nie należy udostępniać odwołanie do rzeczywiste znaki, które tworzą ciąg. Aby uzyskać więcej informacji o sposobie używania `CString` obiektów jako wartości, zobacz [cstring — semantyka](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Pisanie aplikacji, dzięki czemu można kompilować obsługi standardu Unicode lub standardu ANSI, ciągi literałowe kodu za pomocą makra _t —. Aby uzyskać więcej informacji, zobacz [Obsługa zestawu znaków wielobajtowych (MBCS) i Unicode](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> Uzyskiwanie dostępu do poszczególnych znaków CString  
 Możesz uzyskać dostęp pojedynczych znaków w `CString` obiektu za pomocą `GetAt` i `SetAt` metody. Można również użyć operatora elementu lub indeks dolny tablicy ([]) zamiast `GetAt` można pobrać pojedynczych znaków. (To jest podobny do uzyskiwania dostępu do elementów tablicy za pomocą indeksu, tak jak ciągi stylu C standard.) Indeks wartości `CString` znakami zaczynają się od zera.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> Łączenie dwóch cstring — obiekty  
 Do łączenia dwóch `CString` obiekty, użyj concatenation — operatory (+ lub +=), wykonując następujące czynności.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 Co najmniej jednego argumentu operatorów łączenia (+ lub +=) musi być `CString` obiekt, ale można użyć ciągu stałych znaków (na przykład `"big"`) lub **char** (na przykład, "x") dla innych argumentu.  
  
##  <a name="_core_comparing_cstring_objects"></a> Porównywanie cstring — obiekty  
 `Compare` Metody i == — operator dla `CString` są równoważne. `Compare`, **operator ==**, i `CompareNoCase` świadomość MBCS i Unicode; `CompareNoCase` również jest rozróżniana wielkość liter. `Collate` Metody `CString` jest zależne od ustawień regionalnych i często jest mniejsza niż `Compare`. Użyj `Collate` tylko której należy przestrzegać sortowanie reguły określone przez bieżących ustawień regionalnych.  
  
 W poniższej tabeli przedstawiono dostępne [CString](../atl-mfc-shared/reference/cstringt-class.md) porównanie funkcji i ich równoważne funkcje MBCS/Unicode przenośne biblioteki wykonawczej C.  
  
|Cstring — funkcja|MBCS — funkcja|Unicode — funkcja|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT` Klasa szablon definiuje operatory relacyjne (<, \<=, > =, >, ==, i! =), które są dostępne do użycia przez `CString`. Można porównać dwa `CStrings` za pomocą tych operatorów, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> Konwersja z cstring — obiekty  
 Aby uzyskać informacji na temat konwertowania cstring — obiekty na inne typy parametrów, zobacz [porady: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md).  
  
## <a name="using-cstring-with-wcout"></a>Cstring — przy użyciu wcout  
 Aby użyć CString z `wcout` musi jawnie rzutowane obiekt do `const wchar_t*` jak pokazano w poniższym przykładzie:  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 Bez rzutowania `cs` jest traktowany jako `void*` i `wcout` drukuje adres obiektu. To zachowanie jest spowodowane przez subtelne interakcje między argument potrąceń i przeciążenie rozdzielczość szablon używanej w sobie poprawne i zgodność ze standardem C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)   
 [Specjalizacja szablonu](../cpp/template-specialization-cpp.md)   
 [Instrukcje: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)

