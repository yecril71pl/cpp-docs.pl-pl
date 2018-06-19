---
title: Wyliczenie CMFCImagePaintArea::IMAGE_EDIT_MODE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef036c1d619bf85e21edafbd20f20cc27c7c12d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369271"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE — Wyliczenie
Określa tryb rysowania, który umożliwia modyfikowanie obrazu w oknie dialogowym edytora obrazów.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum IMAGE_EDIT_MODE  
{  
    IMAGE_EDIT_MODE_PEN = 0,  
    IMAGE_EDIT_MODE_FILL, 
    IMAGE_EDIT_MODE_LINE, 
    IMAGE_EDIT_MODE_RECT, 
    IMAGE_EDIT_MODE_ELLIPSE, 
    IMAGE_EDIT_MODE_COLOR 
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`IMAGE_EDIT_MODE_PEN`|Używany do rysowania piksele.|  
|`IMAGE_EDIT_MODE_FILL`|Używany do wypełniania wszystkich obszarów sąsiadujących ze sobą, zawierające kolorów w bieżącej lokalizacji kursora.|  
|`IMAGE_EDIT_MODE_LINE`|Używany do rysowania linii.|  
|`IMAGE_EDIT_MODE_RECT`|Używany do rysowania prostokąta.|  
|`IMAGE_EDIT_MODE_ELLIPSE`|Używany do rysowania elipsy.|  
|`IMAGE_EDIT_MODE_COLOR`|Służy do określania bieżący kolor na kolor w bieżącej lokalizacji kursora.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCImagePaintArea` i `CMFCImageEditorDialog` klasy Użyj tego wyliczenia, aby ustawić bieżący tryb rysowania. Tryb rysowania i bieżący kolor są używane do modyfikowania obszar obrazu w oknie dialogowym edytora obrazów. Aby uzyskać więcej informacji na temat `CMFCImagePaintArea` i `CMFCImageEditorDialog`, zobacz [klasy CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md) i [CMFCImageEditorDialog klasy](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
 Po wybraniu koloru z obrazu przy użyciu `IMAGE_EDIT_MODE_COLOR` tryb rysowania, platformę ustawia bieżący tryb rysowania `IMAGE_EDIT_MODE_PEN`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afximagepaintarea.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
