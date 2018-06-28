---
title: Klasa COleIPFrameWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9136f3c57358a71186b196a4223b401e6abad2a9
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040028"
---
# <a name="coleipframewnd-class"></a>Klasa COleIPFrameWnd
Podstawa dla okna do edycji w miejscu aplikacji.  
  
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
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Wywoływane przez platformę, by zmienić położenie okna do edycji w miejscu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa tworzy i pozycje kontrola paski okna aplikacji kontenera dokumentów. Umożliwia on również obsługę powiadomień generowanych w ramach osadzonych [COleResizeBar](../../mfc/reference/coleresizebar-class.md) obiektu, gdy użytkownik zmienia rozmiar okna do edycji w miejscu.  
  
 Aby uzyskać więcej informacji na temat używania `COleIPFrameWnd`, zapoznaj się z artykułem [aktywacji](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cframewnd —](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 Konstruuje `COleIPFrameWnd` obiektu i inicjuje jego informacje o stanie w miejscu, który jest przechowywany w strukturze typu **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) w zestawie Windows SDK.  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
 Wywołania framework `OnCreateControlBars` działać, jeśli element jest aktywowany do edycji w miejscu.  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndFrame*  
 Wskaźnik do okno ramowe aplikacji kontenera.  
  
 *pWndDoc*  
 Wskaźnik do okna poziomie dokumentu kontenera. Może być **NULL** czy aplikacja SDI kontenera.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w przypadku powodzenia; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa. Należy przesłonić tę funkcję, aby wykonać wszelkie specjalnego przetwarzania wymagany, gdy są tworzone paski sterowania.  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 Wywołania framework `RepositionFrame` funkcji członkowskiej ułożyć paski sterowania i zmienia położenie okna do edycji w miejscu, wszystkie z nich jest widoczne.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parametry  
 *lpPosRect*  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu zawierającego w miejscu ramki okna bieżącego współrzędne, w pikselach, względem obszaru klienckiego.  
  
 *lpClipRect*  
 Wskaźnik do `RECT` struktury lub `CRect` obiektu zawierającego w miejscu ramki okna bieżącego Prostokątny wycinek współrzędne, w pikselach, względem obszaru klienckiego.  
  
### <a name="remarks"></a>Uwagi  
 Układ paski kontrolki w oknie kontenera różni się od wykonywane przez okno ramowe innych niż OLE. Okno ramowe innych niż OLE oblicza pozycji paski sterowania i innych obiektów z danego okno ramowe rozmiaru, tak jak wywołanie [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). W obszarze klienta ma pozostałą, po odjęciu jest miejsce na paski sterowania i innych obiektów. A `COleIPFrameWnd` okna, umieszcza paski narzędzi z drugiej strony, zgodnie z obszaru danego klienta. Innymi słowy `CFrameWnd::RecalcLayout` działa "z zewnątrz,", natomiast `COleIPFrameWnd::RepositionFrame` działa "od środka na zewnątrz."  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)
