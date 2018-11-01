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
ms.openlocfilehash: 78b846a6b17fb18f533139e9ac6444babd4baac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498852"
---
# <a name="coleipframewnd-class"></a>Klasa COleIPFrameWnd

Baza dla okna edycji w miejscu aplikacji.

## <a name="syntax"></a>Składnia

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Konstruuje `COleIPFrameWnd` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Wywoływane przez platformę, gdy element jest aktywowany do edycji w miejscu.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Metoda wywoływana przez platformę, by zmienić położenie okna edycji w miejscu.|

## <a name="remarks"></a>Uwagi

Ta klasa tworzy i stanowisk sterowania paski w oknie dokumentu aplikacji kontenera. Obsługuje także powiadomienia generowane przez osadzony [COleResizeBar](../../mfc/reference/coleresizebar-class.md) obiektu, kiedy użytkownik zmienia rozmiar okna edycji w miejscu.

Aby uzyskać więcej informacji na temat korzystania z `COleIPFrameWnd`, zapoznaj się z artykułem [aktywacji](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

Konstruuje `COleIPFrameWnd` obiektu i inicjuje jego informacje o stanie w miejscu, który jest przechowywany w strukturze typu OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [OLEINPLACEFRAMEINFO](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) w zestawie Windows SDK.

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

Struktura wywołuje `OnCreateControlBars` działa, gdy element jest aktywowany do edycji w miejscu.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parametry

*Element pWndFrame*<br/>
Wskaźnik do okno ramowe aplikacji kontenera.

*Element pWndDoc*<br/>
Wskaźnik do okna dokumentu na poziomie kontenera. Może mieć wartości NULL, jeśli kontener jest aplikacją SDI.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera w przypadku powodzenia; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Należy przesłonić tę funkcję, aby wykonywać żadnego specjalnego przetwarzania, wymagane do utworzenia pasków sterowania.

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

Struktura wywołuje `RepositionFrame` funkcja elementu członkowskiego do układania paski sterowania i zmienić położenie okna edycji w miejscu, dzięki czemu wszystkie jest widoczna.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parametry

*lpPosRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt zawierający w miejscu ramki okna bieżące współrzędne, w pikselach, względem pola klienta.

*lpClipRect*<br/>
Wskaźnik do `RECT` struktury lub `CRect` obiekt zawierający w miejscu ramki okna bieżącego prostokątnego wycinka współrzędne, w pikselach, względem pola klienta.

### <a name="remarks"></a>Uwagi

Układ pasków sterowania w oknie kontenera, który różni się od, wykonywane przez okno ramowe / OLE. Okno ramowe / OLE oblicza pozycji paski sterowania i innych obiektów z danego okno ramowe rozmiaru, tak jak wywołanie [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Obszar klienta to, co jeszcze pozostało po odjęciu to miejsce, paskami sterowania i innych obiektów. A `COleIPFrameWnd` okna, z drugiej strony, umieszcza pasków narzędzi zgodnie z obszaru danego klienta. Innymi słowy `CFrameWnd::RecalcLayout` działa "z zewnątrz,", natomiast `COleIPFrameWnd::RepositionFrame` działa "od środka na zewnątrz."

## <a name="see-also"></a>Zobacz też

[Próbki MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
