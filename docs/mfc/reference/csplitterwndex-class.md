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
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363925"
---
# <a name="csplitterwndex-class"></a>Klasa CSplitterWndEx

Reprezentuje dostosowane okno rozdzielacza.

## <a name="syntax"></a>Składnia

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Domyślny konstruktor.|
|`CSplitterWndEx::~CSplitterWndEx`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Wywoływana przez strukturę do rysowania okna rozdzielacza. (Zastępuje [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Uwagi

Zastąpić metodę, `OnDrawSplitter` aby dostosować wygląd komponentów graficznych okna rozdzielacza.

Klasa `CSplitterWndEx` jest używana razem z [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)i [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, które są implementowane przez menedżera wizualnego. Aby spowodować visual manager narysować okno rozdzielacza w `CSplitterWnd` aplikacji, `CSplitterWndEx` zastąpić deklaracje klasy z klasy. W przypadku aplikacji okna ramki klasa okna rozdzielacza jest zadeklarowana w klasie CMainFrame, która znajduje się w mainfrm.h. Na przykład zobacz `OutlookDemo` przykład w katalogu Przykłady.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](cobject-class.md)

[Ccmdtarget](ccmdtarget-class.md)

[Cwnd](cwnd-class.md)

[Csplitterwnd](csplitterwnd-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter

Wywoływana przez strukturę do rysowania okna rozdzielacza.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia. Jeśli ten parametr ma wartość NULL, struktura ponownie rysuje aktywne okno.

*nTyp*<br/>
[w] Jedna z `CSplitterWnd::ESplitType` wartości wyliczenia, która określa element okna rozdzielacza do narysowania. Prawidłowe `splitBox`wartości `splitBar` `splitIntersection`to `splitBorder`, , i .

*Rect*<br/>
[w] Prostokąt ograniczający, który określa wymiary i lokalizację do narysowania określonego elementu okna rozdzielacza.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../hierarchy-chart.md)<br/>
[Klasy](mfc-classes.md)<br/>
[Klasa CSplitterWnd](csplitterwnd-class.md)<br/>
[Klasa CMFCVisualManager](cmfcvisualmanager-class.md)
