---
title: Makra konwersji ciągów
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: 6a84424de81eba2e6ab1e1baf60f567ebf2739ee
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915504"
---
# <a name="string-conversion-macros"></a>Makra konwersji ciągów

Te makra zapewniają funkcje konwersji ciągów.

##  <a name="atl_and_mfc_string_conversion_macros"></a>Makra konwersji ATL i MFC String

Makra konwersji ciągów omówione tutaj są prawidłowe dla ATL i MFC. Aby uzyskać więcej informacji na temat konwersji ciągów MFC [, zobacz TN059: Korzystanie z makr](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) konwersji MFC MBCS/Unicode i [makr MFC oraz Globals](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>Makra konwersji typu String i TEXTMETRIC

Te makra tworzą kopię struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) lub TEXTMETRIC i konwertują ciągi w nowej strukturze na nowy typ ciągu. [](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) Makra przydzielą pamięć na stosie dla nowej struktury i zwracają wskaźnik do nowej struktury.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Uwagi

Na przykład:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

i:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

W nazwach makr typ ciągu w strukturze źródłowej znajduje się po lewej stronie (na przykład **a**), a typ ciągu w strukturze docelowej znajduje się po prawej stronie (na przykład **w**). **Oznacza to** LPStr, że **OLE** oznacza LPOLESTR, **T** oznacza dla LPTStr, a **w p** dla LPWSTR.

W związku z tym DEVMODEA2W `DEVMODE` kopiuje strukturę z ciągami LPSTR `DEVMODE` do struktury z `TEXTMETRIC` ciągami LPWSTR, TEXTMETRICOLE2T kopiuje strukturę z ciągami LPOLESTR `TEXTMETRIC` do struktury z ciągami LPTStr i tak dalej.

Dwa ciągi konwertowane w `DEVMODE` strukturze to nazwa urządzenia (`dmDeviceName`) i nazwa formularza (`dmFormName`). Makra konwersji`dmSize`ciągów również aktualizują rozmiar struktury (). `DEVMODE`

`TEXTMETRIC` Cztery ciągi konwertowane w strukturze są pierwszego znaku (`tmFirstChar`), ostatniego znaku (`tmLastChar`), znaku domyślnego (`tmDefaultChar`) i znaku podziału (`tmBreakChar`).

`DEVMODE` Zachowanie`TEXTMETRIC` makr konwersji ciągów jest zależne od dyrektywy kompilatora, która obowiązuje, jeśli istnieje. Jeśli typy źródłowe i docelowe są takie same, konwersja nie odbywa się. Dyrektywy kompilatora zmieniają **T** i **OLE** w następujący sposób:

|Dyrektywa kompilatora obowiązuje|T zmieni się|Obiekt OLE zostanie|
|----------------------------------|---------------|-----------------|
|brak|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|Unicode i **OLE2ANSI**  **\_**|**W**|**A**|

W poniższej tabeli wymieniono `DEVMODE` makra `TEXTMETRIC` konwersji ciągów i.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
