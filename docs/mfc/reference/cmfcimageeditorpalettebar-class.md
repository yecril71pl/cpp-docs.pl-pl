---
title: Klasa CMFCImageEditorPaletteBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f36a9205cbaa2410dbdc25971a36879412f45ef0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398355"
---
# <a name="cmfcimageeditorpalettebar-class"></a>Klasa CMFCImageEditorPaletteBar

Zapewnia funkcje paska palety okno dialogowe edytora obrazu.

## <a name="syntax"></a>Składnia

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Zwraca wysokość przycisków paska narzędzi. (Przesłania [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Określa, czy pasek narzędzi można wyświetlić przyciski, który został rozszerzony obramowania. (Przesłania [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>Uwagi

Ta klasa nie jest przeznaczona do użycia bezpośrednio w kodzie.

Struktura używa tej klasy, aby wyświetlić pasek palety w okno dialogowe edytora obrazu. Aby uzyskać więcej informacji na temat okno dialogowe edytora obrazu, zobacz [klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afximageeditordialog.h

##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight

Zwraca wysokość przycisków paska narzędzi.

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość każdego przycisku na pasku narzędzi.

##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

Określa, czy pasek narzędzi można wyświetlić przyciski, który został rozszerzony obramowania.

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca wartość FALSE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)
