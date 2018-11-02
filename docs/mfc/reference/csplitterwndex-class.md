---
title: Klasa CSplitterWndEx
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: fa58dbffc3e6416c18b8124f8e5edfe1ce987815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538999"
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