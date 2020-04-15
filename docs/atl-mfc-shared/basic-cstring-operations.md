---
title: Podstawowe operacje na obiekcie CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317960"
---
# <a name="basic-cstring-operations"></a>Podstawowe operacje na obiekcie CString

W tym temacie wyjaśniono następujące podstawowe operacje [CString:](../atl-mfc-shared/reference/cstringt-class.md)

- [Tworzenie obiektów CString ze standardowych ciągów literału C](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Uzyskiwanie dostępu do pojedynczych znaków w cstringu](#_core_accessing_individual_characters_in_a_cstring)

- [Łączenie dwóch obiektów CString](#_core_concatenating_two_cstring_objects)

- [Porównywanie obiektów CString](#_core_comparing_cstring_objects)

- [Konwertowanie obiektów CString](#_core_converting_cstring_objects)

`Class CString`jest oparty na szablonie klasy [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md). `CString`jest **typedef** `CStringT`. Dokładniej, `CString` jest **typedef** *jawnej specjalizacji* `CStringT`, który jest typowym sposobem użycia szablonu klasy do definiowania klasy. Podobnie zdefiniowane `CStringA` klasy `CStringW`są i .

`CString`, `CStringA`i `CStringW` są zdefiniowane w atlstr.h. `CStringT`jest zdefiniowana w cstringt.h.

`CString`, `CStringA`a `CStringW` każdy uzyskać zestaw metod i `CStringT` operatorów zdefiniowanych przez do użycia z danymi ciągu, które obsługują. Niektóre metody duplikowania i, w niektórych przypadkach, przewyższają usługi ciąg bibliotek w czasie wykonywania języka C.

Uwaga: `CString` jest klasą macierzystą. Dla klasy ciągu, która jest używana w projekcie zarządzanym `System.String`c++/cli, należy użyć .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Tworzenie obiektów CString ze standardowych ciągów literału C

Do ciągu literału w stylu `CString` C można przypisać `CString` do niego tak samo, jak można przypisać jeden obiekt do drugiego.

- Przypisz wartość ciągu literału `CString` C do obiektu.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Przypisz wartość `CString` jednego `CString` do innego obiektu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Zawartość `CString` obiektu jest kopiowana, `CString` gdy jeden obiekt jest przypisany do innego. W związku z tym dwa ciągi nie mają wspólnego odwołania do rzeczywistych znaków, które tworzą ciąg. Aby uzyskać więcej informacji `CString` na temat używania obiektów jako wartości, zobacz [Semantyka CString](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Aby napisać aplikację, tak aby można było skompilować dla Unicode lub ANSI, kodować ciągi literału przy użyciu makra _T. Aby uzyskać więcej informacji, zobacz [Obsługa unicode i wielobajtowego zestawu znaków (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Uzyskiwanie dostępu do pojedynczych znaków w cstringu

Dostęp do poszczególnych `CString` znaków w `GetAt` obiekcie można uzyskać przy użyciu metod i. `SetAt` Można również użyć elementu tablicy lub indeksu dolnego, `GetAt` operatora ( [ ] ) zamiast uzyskać pojedyncze znaki. (Przypomina to dostęp do elementów tablicy według indeksu, tak jak w standardowych ciągach w stylu C). Wartości indeksu dla `CString` znaków są oparte na wartościach zerowych.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Łączenie dwóch obiektów CString

Aby łączyć `CString` dwa obiekty, należy użyć operatorów łączenia (+ lub +=), w następujący sposób.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Co najmniej jeden argument operatorów łączenia (+ lub `CString` +=) musi być obiektem, ale `"big"`dla innego argumentu można użyć stałego ciągu znaków (na przykład ) lub **znaku** (na przykład 'x').

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Porównywanie obiektów CString

Metoda `Compare` i == operator `CString` dla są równoważne. `Compare`, **operator==** `CompareNoCase` i są MBCS i Unicode świadomy; `CompareNoCase` jest również niewrażliwa na argumenty. Metoda `Collate` jest `CString` wrażliwa na ustawienia regionalne `Compare`i jest często wolniejsza niż . Używaj `Collate` tylko wtedy, gdy musisz przestrzegać reguł sortowania określonych przez bieżące ustawienia regionalne.

W poniższej tabeli przedstawiono dostępne funkcje porównania [CString](../atl-mfc-shared/reference/cstringt-class.md) i ich równoważne funkcje przenośne Unicode/MBCS w bibliotece czasu wykonywania języka C.

|CString, funkcja|MBCS, funkcja|Unicode, funkcja|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Szablon `CStringT` klasy definiuje operatory relacyjne (<, \<=, >=, >, ==, i !=), które `CString`są dostępne do użycia przez . Można porównać `CStrings` dwa za pomocą tych operatorów, jak pokazano w poniższym przykładzie.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Konwertowanie obiektów CString

Aby uzyskać informacje dotyczące konwertowania obiektów CString na inne typy ciągów, zobacz [Jak: Konwertowanie między różnymi typami ciągów](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Korzystanie z CString z wcout

Aby użyć CString `wcout` z należy jawnie rzutować obiekt do, `const wchar_t*` jak pokazano w poniższym przykładzie:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Bez odlewu, `cs` jest `void*` traktowany jako i `wcout` drukuje adres obiektu. To zachowanie jest spowodowane przez subtelne interakcje między dedukcji argument szablonu i przeciążenia rozpoznawania, które same w sobie są poprawne i zgodne ze standardem C++.

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Specjalizacja szablonu](../cpp/template-specialization-cpp.md)<br/>
[Instrukcje: konwertowanie między rozmaitymi typami ciągów](../text/how-to-convert-between-various-string-types.md)
