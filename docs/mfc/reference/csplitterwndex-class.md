---
title: Klasa CSplitterWndEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df892a3d3f038655f37b78fa88babb09d50df2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373484"
---
# <a name="csplitterwndex-class"></a>Klasa CSplitterWndEx



Przedstawia dostosowane okno rozdzielacza.

## <a name="syntax"></a>Składnia

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Domyślny konstruktor.|
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Metoda wywoływana przez platformę, by narysować okno rozdzielacza. (Przesłania [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Uwagi

Zastąp `OnDrawSplitter` metodę w celu dostosowania wyglądu graficznego składniki okno rozdzielacza.

`CSplitterWndEx` Klasa jest używana razem z [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), i [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, które są implementowany przez Menedżer wizualnego. Aby spowodować, że Menedżer wizualnego narysować okno rozdzielacza, w aplikacji, należy zastąpić deklaracje `CSplitterWnd` klasy `CSplitterWndEx` klasy. W przypadku aplikacji okna ramki klasy okna podziału jest zadeklarowany w cmainframe — klasa, która znajduje się w mainfrm.h. Aby uzyskać przykład, zobacz `OutlookDemo` próbki w katalogu przykładów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

Metoda wywoływana przez platformę, by narysować okno rozdzielacza.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia. Jeśli ten parametr ma wartość NULL, w ramach odrysowuje aktywnego okna.

*nNie*<br/>
[in] Jedną z `CSplitterWnd::ESplitType` wartości wyliczenia określających element okno rozdzielacza, aby narysować. Prawidłowe wartości to `splitBox`, `splitBar`, `splitIntersection`, i `splitBorder`.

*Rect*<br/>
[in] Prostokąt otaczający, określający, wymiary i lokalizację, aby rysować element okno rozdzielacza określony.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Klasy](mfc-classes.md)<br/>
[Klasa CSplitterWnd](csplitterwnd-class.md)<br/>
[Klasa CMFCVisualManager](cmfcvisualmanager-class.md)