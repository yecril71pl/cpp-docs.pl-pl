---
title: "Cstring — podstawowe operacje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 566f2d29da9ff8422b8a29178f63a553bfe33668
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="basic-cstring-operations"></a>Cstring — podstawowe operacje
W tym temacie opisano następujące basic [cstring —](../atl-mfc-shared/reference/cstringt-class.md) operacje:  
  
- [Tworzenie cstring — obiekty z standardowe C ciągi literału](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [Uzyskiwanie dostępu do poszczególnych znaków cstring —](#_core_accessing_individual_characters_in_a_cstring)  
  
- [Łączenie dwóch cstring — obiekty](#_core_concatenating_two_cstring_objects)  
  
- [Porównywanie cstring — obiekty](#_core_comparing_cstring_objects)  
  
- [Konwertowanie cstring — obiekty](#_core_converting_cstring_objects)  
  
 `Class CString`jest oparty na szablonie klasy [CStringT klasy](../atl-mfc-shared/reference/cstringt-class.md). `CString`jest `typedef` z `CStringT`. Bardziej dokładnie `CString` jest `typedef` z *jawna specjalizacja* z `CStringT`, który jest typowym sposobem umożliwia definiowanie klasy szablonu klasy. Podobnie zdefiniowanych klas są `CStringA` i `CStringW`.  
  
 `CString`, `CStringA`, i `CStringW` są zdefiniowane w atlstr.h. `CStringT`jest zdefiniowany w cstringt.h.  
  
 `CString`, `CStringA`, i `CStringW` uzyskania każdego zestawu metod i operatory zdefiniowane przez `CStringT` dla danych ciąg ich obsługi. Niektóre metody duplikatów, a w niektórych przypadkach przekroczenia usług ciąg biblioteki wykonawcze języka C.  
  
 Uwaga: `CString` jest klasą macierzystego. Dla klasy ciąg, który ma być używany w języku C + +/ CLI zarządzanego projektu, użyj `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Tworzenie cstring — obiekty z ciągi literału Standard C  
 Ciągi literałów w stylu języka C do można przypisać `CString` tylko należy przypisać jeden `CString` obiektu do innego.  
  
-   Przypisanie wartości literału ciągu C do `CString` obiektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   Przypisywanie wartości jednego `CString` do innego `CString` obiektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     Zawartość `CString` obiektu są kopiowane, gdy dla jednego `CString` obiekt jest przypisany do innego. Dwa ciągi nie udostępniaj w związku z tym odwołaniem do rzeczywiste znaki, które tworzą ciąg. Aby uzyskać więcej informacji o sposobie używania `CString` obiektów jako wartości, zobacz [semantyki cstring —](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Pisanie aplikacji, dzięki czemu mogą być kompilowane Unicode lub ANSI, ciągi literału kodu za pomocą makra _t —. Aby uzyskać więcej informacji, zobacz [Unicode i pomocy technicznej ustawić znaków wielobajtowych (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a>Uzyskiwanie dostępu do poszczególnych znaków cstring —  
 Można uzyskać dostępu do poszczególnych znaków `CString` obiektu za pomocą `GetAt` i `SetAt` metody. Można również użyć operatora elementu lub indeks dolny, tablicy ([]) zamiast `GetAt` można uzyskać znaki. (To jest podobny do uzyskiwania dostępu do elementów tablicy przez indeks, tak jak standardowe ciągów w stylu języka C.) Indeks wartości `CString` znaków jest liczony od zera.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a>Łączenie dwóch cstring — obiekty  
 Do łączenia dwóch `CString` obiektów, użyj operatory łączenia (+ lub +=) w następujący sposób.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 Co najmniej jeden argument operatory łączenia (+ lub +=) musi być `CString` obiekt, ale można użyć ciągu znaków stała (na przykład `"big"`) lub `char` (na przykład "x") dla innych argumentu.  
  
##  <a name="_core_comparing_cstring_objects"></a>Porównywanie cstring — obiekty  
 `Compare` — Metoda i == — operator dla `CString` są równoważne. `Compare`, `operator==`, i `CompareNoCase` wiedzą MBCS i Unicode; `CompareNoCase` jest również bez uwzględniania wielkości liter. `Collate` Metody `CString` jest zależne od ustawień regionalnych i często jest mniejsza niż `Compare`. Użyj `Collate` tylko gdy należy przestrzegać sortowania reguły określone przez bieżące ustawienia regionalne.  
  
 W poniższej tabeli przedstawiono dostępne [cstring —](../atl-mfc-shared/reference/cstringt-class.md) porównanie funkcji i ich równoważne funkcje Unicode/MBCS — portable biblioteki wykonawcze języka C.  
  
|Cstring — funkcja|MBCS — funkcja|Unicode — funkcja|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT` Szablonu klasy definiuje operatory relacyjne (<, \<=, > =, >, =, i! =), które są dostępne do użycia przez `CString`. Możesz porównać dwa `CStrings` za pomocą tych operatorów, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a>Konwertowanie cstring — obiekty  
 Uzyskać informacji na temat konwertowania cstring — obiekty na inne typy string, zobacz [porady: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md).  
  
## <a name="using-cstring-with-wcout"></a>Przy użyciu obiektu CString z wcout  
 Aby użyć obiektu CString z `wcout` musi jawnie rzutowanie tego obiektu na `const wchar_t*` jak pokazano w poniższym przykładzie:  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 Brak rzutowania `cs` jest traktowany jako `void*` i `wcout` drukuje adres obiektu. To zachowanie jest spowodowane niewielkie interakcje między szablonu argument wnioskowanie przeciążenia rozpoznawania i które są w sobie poprawne a zgodność C++ standard.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Klasa CStringT](../atl-mfc-shared/reference/cstringt-class.md)   
 [Specjalizacja szablonu](../cpp/template-specialization-cpp.md)   
 [Porady: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)

