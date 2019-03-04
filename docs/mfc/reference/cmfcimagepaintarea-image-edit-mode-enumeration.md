---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE — Wyliczenie
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 372a1df6500f4d7219c89d8f82425246c2236514
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272142"
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

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
