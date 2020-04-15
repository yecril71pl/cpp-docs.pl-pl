---
title: Klasa COleIPFrameWnd
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374955"
---
# <a name="coleipframewnd-class"></a>Klasa COleIPFrameWnd

Podstawa okna edycji aplikacji w miejscu.

## <a name="syntax"></a>Składnia

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Konstruuje `COleIPFrameWnd` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Wywoływana przez strukturę, gdy element jest aktywowany do edycji w miejscu.|
|[COleIPFrameWnd::Zmień położenieFrame](#repositionframe)|Wywoływana przez strukturę do zmiany położenia okna edycji w miejscu.|

## <a name="remarks"></a>Uwagi

Ta klasa tworzy i umieszcza paski sterowania w oknie dokumentu aplikacji kontenera. Obsługuje również powiadomienia generowane przez osadzony [obiekt COleResizeBar,](../../mfc/reference/coleresizebar-class.md) gdy użytkownik zmienić rozmiar okna edycji w miejscu.

Aby uzyskać więcej `COleIPFrameWnd`informacji na temat korzystania z programu , zobacz artykuł [Aktywacja](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

Konstruuje `COleIPFrameWnd` obiekt i inicjuje jego informacje o stanie w miejscu, który jest przechowywany w strukturze typu OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) w windows SDK.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars

Struktura wywołuje `OnCreateControlBars` funkcję, gdy element jest aktywowany do edycji w miejscu.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parametry

*pWndFrame (Klatka pWndFrame)*<br/>
Wskaźnik do okna ramki aplikacji kontenera.

*pWndDoc (ps.*<br/>
Wskaźnik do okna na poziomie dokumentu kontenera. Może mieć wartość NULL, jeśli kontener jest aplikacją SDI.

### <a name="return-value"></a>Wartość zwracana

Nonzero na sukces; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie wymagane podczas tworzenia prętów sterujących.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::Zmień położenieFrame

Struktura wywołuje `RepositionFrame` funkcję elementu członkowskiego, aby rozłożyć paski sterowania i zmienić położenie okna edycji w miejscu, tak aby wszystko było widoczne.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu zawierającego bieżące współrzędne położenia okna ramki w miejscu w pikselach względem obszaru klienta.

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury `CRect` lub obiektu zawierającego bieżące współrzędne wycinka i prostokąta okna w miejscu, w pikselach względem obszaru klienta.

### <a name="remarks"></a>Uwagi

Układ prętów sterujących w oknie kontenera różni się od tego wykonywanego przez okno ramki inne niż OLE. Okno ramki inne niż OLE oblicza pozycje prętów sterujących i innych obiektów z danego rozmiaru okna ramki, tak jak w wywołaniu [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Obszar klienta jest tym, co pozostaje po odjęciu miejsca na pręty sterujące i inne obiekty. Okno, `COleIPFrameWnd` z drugiej strony, umieszcza paski narzędzi zgodnie z danym obszarem klienta. Innymi słowy, `CFrameWnd::RecalcLayout` działa "z zewnątrz w", podczas gdy `COleIPFrameWnd::RepositionFrame` działa "od wewnątrz na zewnątrz."

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
