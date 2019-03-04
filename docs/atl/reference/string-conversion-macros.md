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
ms.openlocfilehash: 889f8459e81418197420bc2efd410225d4f220bc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271765"
---
# <a name="string-conversion-macros"></a>Makra konwersji ciągów

Te makra wprowadzić parametry funkcji konwersji.

##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL i makr konwersji ciągu MFC

Makra konwersji ciągów omówionych w tym miejscu są prawidłowe dla biblioteki ATL i MFC. Aby uzyskać więcej informacji na temat konwersji ciągów MFC, zobacz [TN059: Przy użyciu makr konwersji MFC MBCS/Unicode](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) i [makr MFC i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE i makra konwersji ciągów TEXTMETRIC

Te makra Utwórz kopię [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) lub [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) struktury i konwertowanie ciągów w ramach nowej struktury na nowy typ ciągu. Makra przydzielić pamięci na stosie dla nowej struktury i zwracają wskaźnik do nowej struktury.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Uwagi

Na przykład:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

i:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

W polu nazwy makra typ ciągu w strukturze źródłowej jest po lewej stronie (na przykład **A**) i typ ciągu w strukturze docelowej jest po prawej stronie (na przykład **W**). **A** to LPSTR, **OLE** oznacza LPOLESTR, **T** oznacza LPTSTR, i **W** oznacza LPWSTR.

W związku z tym, kopiuje DEVMODEA2W `DEVMODE` strukturę LPSTR ciągów do `DEVMODE` struktury z ciągami LPWSTR, kopie TEXTMETRICOLE2T `TEXTMETRIC` strukturę LPOLESTR ciągów do `TEXTMETRIC` struktury z ciągami LPTSTR i tak dalej.

Dwa ciągi w `DEVMODE` struktury są nazwy urządzenia (`dmDeviceName`) i nazwa formularza (`dmFormName`). `DEVMODE` Makra konwersji ciągów również zaktualizować rozmiar struktury (`dmSize`).

Cztery ciągi w `TEXTMETRIC` struktury jest pierwszym znakiem (`tmFirstChar`), ostatni znak (`tmLastChar`), domyślny znak (`tmDefaultChar`), a znak podziału (`tmBreakChar`).

Zachowanie `DEVMODE` i `TEXTMETRIC` makra konwersji ciągu jest zależna od dyrektywy kompilatora, w efekcie Jeśli istnieje. Jeśli typy źródłowy i docelowy są takie same, odbywa się bez konwersji. Dyrektywy kompilatora zmienić **T** i **OLE** w następujący sposób:

|Dyrektywy kompilatora efektu|Staje się T|Staje się OLE|
|----------------------------------|---------------|-----------------|
|brak|**A**|**W**|
|**\_UNICODE**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|**\_UNICODE** i **OLE2ANSI**|**W**|**A**|

W poniższej tabeli wymieniono `DEVMODE` i `TEXTMETRIC` makra konwersji ciągów.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
