---
title: Makra konwersji ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 917afc7dae7a0ed96d5d5cc476b4f8394abe8913
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362978"
---
# <a name="string-conversion-macros"></a>Makra konwersji ciągu

Te makra Podaj funkcji konwersji.  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL i makr konwersji MFC ciągu

Makra konwersji ciągu omówione w tym miejscu są prawidłowe dla ATL i MFC. Aby uzyskać więcej informacji o konwersji ciągu MFC, zobacz [TN059: za pomocą makr konwersji MFC MBCS/Unicode](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) i [makr MFC i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE i makra konwersji ciągu TEXTMETRIC

Te makra Utwórz kopię [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) lub [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) struktury i konwertowanie ciągów w strukturze nowe na nowy typ ciągu. Makra przydzielić pamięci na stosie dla nowej struktury i zwraca wskaźnik do nowej struktury.  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Uwagi

Na przykład:  
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
i:  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
W nazwach makro typu ciąg w strukturze źródła jest po lewej stronie (na przykład **A**) i jest typ ciąg w strukturze docelowej po prawej stronie (na przykład **W**). **A** oznacza `LPSTR`, **OLE** oznacza `LPOLESTR`, **T** oznacza `LPTSTR`, i **W** oznacza `LPWSTR`.  
  
W związku z tym **DEVMODEA2W** kopie `DEVMODE` struktury z `LPSTR` ciągi do `DEVMODE` struktury z `LPWSTR` ciągów, **TEXTMETRICOLE2T** kopiuje `TEXTMETRIC`struktury z `LPOLESTR` ciągi do `TEXTMETRIC` struktury z `LPTSTR` ciągów itd.  
  
Dwa ciągi w `DEVMODE` struktury są nazwy urządzenia (`dmDeviceName`) i nazwa formularza (`dmFormName`). `DEVMODE` Makra konwersji ciągu również zaktualizować rozmiar struktury (`dmSize`).  
  
Cztery ciągi w `TEXTMETRIC` struktury są pierwszego znaku (`tmFirstChar`), po ostatnim znaku (`tmLastChar`), domyślny znak (`tmDefaultChar`) i znak podziału (`tmBreakChar`).
  
Zachowanie `DEVMODE` i `TEXTMETRIC` makra konwersji ciągu jest zależna od dyrektywy kompilatora w rezultacie ewentualne. Jeśli typy źródłowy i docelowy są takie same, odbywa się bez konwersji. Dyrektywy kompilatora zmienić **T** i **OLE** w następujący sposób:  
  
|Dyrektywy kompilatora w obiekcie|Staje się T|Staje się OLE|  
|----------------------------------|---------------|-----------------|  
|brak|**A**|**W**|  
|**\_UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_UNICODE** i **OLE2ANSI**|**W**|**A**|  
  
 W poniższej tabeli wymieniono `DEVMODE` i `TEXTMETRIC` ciągu makra konwersji.  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
