---
title: Wyliczanie Cmfcimagepaintarea::image_edit_mode | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b87b0c8c179e2982c450d244c50ea89dad2a596a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848609"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE — Wyliczenie
Określa tryb rysowania, którego używasz do modyfikowania obrazu w okno dialogowe edytora obrazu.  
  
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
|IMAGE_EDIT_MODE_PEN|Używany do rysowania poszczególnych pikseli.|  
|IMAGE_EDIT_MODE_FILL|Używany do wypełniania wszystkie sąsiadujące obszary, które zawiera koloru w bieżącej lokalizacji kursora.|  
|IMAGE_EDIT_MODE_LINE|Używane, aby narysować linię.|  
|IMAGE_EDIT_MODE_RECT|Używane, aby narysować prostokąt.|  
|IMAGE_EDIT_MODE_ELLIPSE|Używane, aby narysować elipsę.|  
|IMAGE_EDIT_MODE_COLOR|Używane, aby ustawić bieżący kolor na kolor w bieżącej lokalizacji kursora.|  
  
### <a name="remarks"></a>Uwagi  
 `CMFCImagePaintArea` i `CMFCImageEditorDialog` klasy używają tego wyliczenia, aby ustawić bieżący tryb rysowania. Tryb rysowania i bieżący kolor służą do modyfikowania obszar obrazu w okno dialogowe edytora obrazu. Aby uzyskać więcej informacji na temat `CMFCImagePaintArea` i `CMFCImageEditorDialog`, zobacz [klasa CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md) i [klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
 Po wybraniu koloru z obrazu w trybie rysowania IMAGE_EDIT_MODE_COLOR ramach ustawia bieżący tryb rysowania IMAGE_EDIT_MODE_PEN.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afximagepaintarea.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
