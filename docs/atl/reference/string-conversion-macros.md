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
ms.openlocfilehash: 60cccebf4e1db8369ea5a88f04a37b96838ff49f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835158"
---
# <a name="string-conversion-macros"></a>Makra konwersji ciągów

Te makra zapewniają funkcje konwersji ciągów.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a> Makra konwersji ATL i MFC String

Makra konwersji ciągów omówione tutaj są prawidłowe dla ATL i MFC. Aby uzyskać więcej informacji na temat konwersji ciągów MFC, zobacz [TN059: Using MFC MBCS/Unicode MACROS](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) i [makr MFC i Globals](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a> Makra konwersji typu String i TEXTMETRIC

Te makra tworzą kopię struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) lub [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) i konwertują ciągi w nowej strukturze na nowy typ ciągu. Makra przydzielą pamięć na stosie dla nowej struktury i zwracają wskaźnik do nowej struktury.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Uwagi

Na przykład:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

i:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

W nazwach makr typ ciągu w strukturze źródłowej znajduje się po lewej stronie (na przykład **a**), a typ ciągu w strukturze docelowej znajduje się po prawej stronie (na przykład **w**). **Oznacza to** LPStr, że **OLE** oznacza LPOLESTR, **T** oznacza dla LPTStr, a **w p** dla LPWSTR.

W związku z tym DEVMODEA2W kopiuje `DEVMODE` strukturę z ciągami LPSTR do `DEVMODE` struktury z ciągami LPWSTR, TEXTMETRICOLE2T kopiuje `TEXTMETRIC` strukturę z ciągami LPOLESTR do `TEXTMETRIC` struktury z ciągami LPTStr i tak dalej.

Dwa ciągi konwertowane w `DEVMODE` strukturze to nazwa urządzenia ( `dmDeviceName` ) i nazwa formularza ( `dmFormName` ). `DEVMODE`Makra konwersji ciągów również aktualizują rozmiar struktury ( `dmSize` ).

Cztery ciągi konwertowane w `TEXTMETRIC` strukturze są pierwszego znaku ( `tmFirstChar` ), ostatniego znaku ( `tmLastChar` ), znaku domyślnego ( `tmDefaultChar` ) i znaku podziału ( `tmBreakChar` ).

Zachowanie `DEVMODE` `TEXTMETRIC` makr konwersji ciągów jest zależne od dyrektywy kompilatora, która obowiązuje, jeśli istnieje. Jeśli typy źródłowe i docelowe są takie same, konwersja nie odbywa się. Dyrektywy kompilatora zmieniają **T** i **OLE** w następujący sposób:

|Dyrektywa kompilatora obowiązuje|T zmieni się|Obiekt OLE zostanie|
|----------------------------------|---------------|-----------------|
|brak|**A**|**K**|
|**\_UNICODE**|**K**|**K**|
|**OLE2ANSI**|**A**|**A**|
|** \_ Unicode** i **OLE2ANSI**|**K**|**A**|

W poniższej tabeli wymieniono `DEVMODE` `TEXTMETRIC` makra konwersji ciągów i.

|`DEVMODE` makro|`TEXTMETRIC` makro|
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
