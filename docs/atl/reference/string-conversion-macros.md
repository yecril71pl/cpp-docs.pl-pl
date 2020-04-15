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
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325850"
---
# <a name="string-conversion-macros"></a>Makra konwersji ciągów

Te makra zapewniają funkcje konwersji ciągów.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>Makra konwersji ciągów ATL i MFC

Makra konwersji ciągów omówione w tym miejscu są prawidłowe dla ATL i MFC. Aby uzyskać więcej informacji na temat konwersji ciągów MFC, zobacz [TN059: Korzystanie z makr konwersji MFC MBCS/Unicode](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) oraz [makr i wartości globalnych MFC](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>Makra konwersji ciągów DEVMODE i TEXTMETRIC

Te makra tworzą kopię struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) lub [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) i konwertują ciągi w nowej strukturze na nowy typ ciągu. Makra przydzielić pamięć na stosie dla nowej struktury i zwraca wskaźnik do nowej struktury.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Uwagi

Przykład:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

i:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

W nazwach makr typ ciągu w strukturze źródłowej znajduje się po lewej stronie (na przykład **A),** a typ ciągu w strukturze docelowej znajduje się po prawej stronie (na przykład **W**). **Skrót** lpstr, **OLE** oznacza LPOLESTR, **T** oznacza LPTSTR, a **W** oznacza LPWSTR.

W ten sposób DEVMODEA2W kopiuje `DEVMODE` strukturę `DEVMODE` z ciągami LPSTR do struktury z ciągami `TEXTMETRIC` LPWSTR, TEXTMETRICOLE2T kopiuje strukturę z ciągami LPOLESTR w strukturę `TEXTMETRIC` z ciągami LPTSTR i tak dalej.

Dwa ciągi przekonwertowane w `DEVMODE` strukturze`dmDeviceName`to nazwa urządzenia`dmFormName`( ) i nazwa formularza ( ). Makra `DEVMODE` konwersji ciągów aktualizują`dmSize`również rozmiar struktury ( ).

Cztery ciągi konwertowane w `TEXTMETRIC` strukturze`tmFirstChar`są pierwszym znakiem`tmLastChar`( ),`tmDefaultChar`ostatnim znakiem (`tmBreakChar`), znakiem domyślnym ( i znakiem przerwania ( ).

Zachowanie `DEVMODE` makr `TEXTMETRIC` konwersji i ciągów zależy od dyrektywy kompilatora w życie, jeśli istnieje. Jeśli typy źródłowe i docelowe są takie same, nie ma miejsca konwersja. Dyrektywy kompilatora zmienić **T** i **OLE** w następujący sposób:

|Obowiązująca dyrektywa kompilatora|T staje się|OLE staje się|
|----------------------------------|---------------|-----------------|
|brak|**A**|**W**|
|**\_Unicode**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE i **OLE2ANSI** ** \_**|**W**|**A**|

W poniższej `DEVMODE` tabeli wymieniono makra konwersji i `TEXTMETRIC` ciągów.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W (TEKSTMETRICA2W)|
|DEVMODEOLE2T|TEXTMETRICOLE2T (TEKSTMETRICOLE2T)|
|DEVMODET2OLE (DEVMODET2OLE)|TEXTMETRICT2OLE (TEKSTMETRICT2OLE)|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
