---
title: Podstawowe operacje CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: fa46e82f19d87c49f652779d0e86e78549935965
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220902"
---
# <a name="basic-cstring-operations"></a>Podstawowe operacje CString

W tym temacie objaśniono następujące podstawowe operacje [CString](../atl-mfc-shared/reference/cstringt-class.md) :

- [Tworzenie obiektów CString ze standardowych ciągów literału C](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Uzyskiwanie dostępu do pojedynczych znaków w CString](#_core_accessing_individual_characters_in_a_cstring)

- [Łączenie dwóch obiektów CString](#_core_concatenating_two_cstring_objects)

- [Porównywanie obiektów CString](#_core_comparing_cstring_objects)

- [Konwertowanie obiektów CString](#_core_converting_cstring_objects)

`Class CString`jest oparty na [klasie CStringT](../atl-mfc-shared/reference/cstringt-class.md)szablonu klasy. `CString`ma wartość **`typedef`** `CStringT` . Dokładniej, `CString` jest to **`typedef`** *Jawna specjalizacja* `CStringT` , która jest powszechnym sposobem użycia szablonu klasy do zdefiniowania klasy. Podobne zdefiniowane klasy to `CStringA` i `CStringW` .

`CString`, `CStringA` , i `CStringW` są zdefiniowane w pliku atlstr. h. `CStringT`jest zdefiniowany w CStringT. h.

`CString`, `CStringA` , i `CStringW` każdy z nich Pobiera zestaw metod i operatorów zdefiniowanych przez `CStringT` program do użycia z danymi ciągu, które obsługują. Niektóre metody duplikują i, w niektórych przypadkach, przekraczają usługi ciągów bibliotek uruchomieniowych C.

Uwaga: `CString` jest klasą natywną. Dla klasy String, która jest używana w projekcie zarządzanym C++/CLI, użyj `System.String` .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Tworzenie obiektów CString ze standardowych ciągów literału C

Można przypisać ciągi literału w stylu C do `CString` samego siebie, tak jak można przypisać jeden `CString` obiekt do innego.

- Przypisz wartość ciągu literału C do `CString` obiektu.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Przypisz wartość jednego `CString` do innego `CString` obiektu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Zawartość `CString` obiektu jest kopiowana po `CString` przypisaniu jednego obiektu do drugiego. W związku z tym dwa ciągi nie współdzielą odwołania do rzeczywistych znaków, które tworzą ciąg. Aby uzyskać więcej informacji o sposobach używania `CString` obiektów jako wartości, zobacz [semantyka CString](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Aby napisać aplikację tak, aby mogła być skompilowana dla Unicode lub dla ANSI, ciągi literałów kodu przy użyciu makra _T. Aby uzyskać więcej informacji, zobacz [Obsługa zestawów znaków Unicode i wielobajtowych (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Uzyskiwanie dostępu do pojedynczych znaków w CString

Dostęp do pojedynczych znaków w obiekcie można uzyskać `CString` przy użyciu `GetAt` metod i `SetAt` . Można również użyć elementu Array lub indeksu dolnego ([]) zamiast, `GetAt` Aby uzyskać poszczególne znaki. (To przypomina dostęp do elementów tablicy według indeksu, jak w standardowych ciągach w stylu C). Wartości indeksu dla `CString` znaków są zależne od zera.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Łączenie dwóch obiektów CString

Aby połączyć dwa `CString` obiekty, użyj operatorów łączenia (+ lub + =) w następujący sposób.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Co najmniej jeden argument w operatorach łączenia (+ lub + =) musi być `CString` obiektem, ale można użyć stałego ciągu znaków (na przykład `"big"` ) lub znaku **`char`** (na przykład "x") dla drugiego argumentu.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Porównywanie obiektów CString

`Compare`Metoda i operator = = `CString` są równoważne. `Compare`**Operatory = =** i `CompareNoCase` są MBCS i obsługujące kod Unicode; uwzględnia `CompareNoCase` również wielkość liter. `Collate`Metoda `CString` jest zależna od ustawień regionalnych i jest często wolniejsza niż `Compare` . Używaj `Collate` tylko wtedy, gdy musisz przestrzegać reguł sortowania określonych przez bieżące ustawienia regionalne.

W poniższej tabeli przedstawiono dostępne funkcje porównania [CString](../atl-mfc-shared/reference/cstringt-class.md) oraz ich równoważne funkcje w formacie Unicode/MBCS-Portable w bibliotece wykonawczej C.

|CString, funkcja|MBCS, funkcja|Funkcja Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`Szablon klasy definiuje operatory relacyjne (<, \<=, > =, >, = = i! =), które są dostępne do użytku przez program `CString` . Można porównać dwie przy `CStrings` użyciu tych operatorów, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Konwertowanie obiektów CString

Aby uzyskać informacje na temat konwertowania obiektów CString na inne typy ciągów, zobacz [How to: converting Between String Types](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Używanie CString z wcout

Aby użyć CString z `wcout` , musisz jawnie rzutować obiekt na taki `const wchar_t*` , jak pokazano w następującym przykładzie:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Bez rzutowania, `cs` jest traktowane jako **`void*`** a i `wcout` drukuje adres obiektu. To zachowanie jest spowodowane przez delikatne interakcje między odliczeniami argumentów szablonu i rozpoznawaniem przeciążenia, które są poprawne i zgodne ze standardem C++.

## <a name="see-also"></a>Zobacz także

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Klasa CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Specjalizacja szablonu](../cpp/template-specialization-cpp.md)<br/>
[Instrukcje: konwertowanie różnych typów ciągów](../text/how-to-convert-between-various-string-types.md)
