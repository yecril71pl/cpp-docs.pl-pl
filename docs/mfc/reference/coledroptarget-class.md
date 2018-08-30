---
title: Klasa COleDropTarget | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 218b03ed1e1c69dd7b365e9c2526aef5b1145aed
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218492"
---
# <a name="coledroptarget-class"></a>Klasa COleDropTarget
Udostępnia mechanizm komunikacji między trybem okna a bibliotekami OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Konstruuje `COleDropTarget` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Wywołuje się, gdy kursor po raz pierwszy najedzie okna.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Wywołuje się, gdy kursor jest przeciągany poza okna.|  
|[COleDropTarget::OnDragOver](#ondragover)|Wywołuje się wielokrotnie, gdy kursor jest przeciągany nad oknem.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Wywołuje się, by określić czy kursor jest przeciągany w regionie przewijania, okna.|  
|[COleDropTarget::OnDrop](#ondrop)|Wywołuje się, gdy dane są przenoszone do okna, domyślny program obsługi.|  
|[COleDropTarget::OnDropEx](#ondropex)|Wywołuje się, gdy dane są przenoszone do okna obsługi początkowej.|  
|[COleDropTarget::Register](#register)|Rejestruje okna jako prawidłowe miejsca docelowego.|  
|[COleDropTarget::Revoke](#revoke)|Powoduje, że okno zaprzestania są prawidłowe miejsca docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Tworzenie obiektu tej klasy pozwala oknu na akceptowanie danych za pośrednictwem mechanizmu OLE przeciągania i upuszczania.  
  
 Aby dostać okno aby zaakceptować poleceń drop, należy najpierw utworzyć obiekt `COleDropTarget` klasy, a następnie wywołaj [zarejestrować](#register) funkcji za pomocą wskaźnika do żądaną `CWnd` obiektu jako jedyny parametr.  
  
 Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą mechanizmu OLE, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget  
 Tworzy obiekt klasy `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj [zarejestrować](#register) można powiązać ten obiekt z okna.  
  
##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter  
 Wywoływane przez platformę, gdy kursor jest najpierw przeciągany do okna.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Punkty do okna kursora jest wprowadzenie.  
  
 *pDataObject*  
 Wskazuje obiekt danych zawierające dane, które można było porzucić.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Zawiera bieżącą lokalizację kursor w współrzędne klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt, który byłby wynikiem, jeśli podjęto zrzutu w lokalizacji określonej przez *punktu*. Może być co najmniej jeden z następujących czynności:  
  
- DROPEFFECT_NONE zrzutu będzie niedozwolone.  
  
- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
  
- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
  
- Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.  
  
- Operacja przewijania przeciągania A DROPEFFECT_SCROLL może nastąpić lub odbywa się w elemencie docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby umożliwić listy operacji w oknie. Domyślna implementacja wywołuje [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), która po prostu zwraca DROPEFFECT_NONE domyślnie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) w zestawie Windows SDK.  
  
##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave  
 Wywoływane przez platformę, gdy kursor opuszcza okna operację przeciągania w czasie działania.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Opuszcza punktów do okna kursora.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli mają specjalne zachowanie podczas operacji przeciągania pozostawia określonego okna. Domyślna implementacja ta funkcja wywołuje [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragLeave](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragleave) w zestawie Windows SDK.  
  
##  <a name="ondragover"></a>  COleDropTarget::OnDragOver  
 Wywoływane przez platformę, gdy kursor jest przeciągany nad oknem.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskazuje okna, nad którym znajduje się kursor.  
  
 *pDataObject*  
 Wskazuje obiekt danych, który zawiera dane, które ma zostać przerwane.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Zawiera bieżącą lokalizację kursor w współrzędne klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt, który byłby wynikiem, jeśli podjęto zrzutu w lokalizacji określonej przez *punktu*. Może być co najmniej jeden z następujących czynności:  
  
- DROPEFFECT_NONE zrzutu będzie niedozwolone.  
  
- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
  
- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
  
- Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.  
  
- DROPEFFECT_SCROLL wskazuje, że operacji przeciągania przewijania może nastąpić lub odbywa się w elemencie docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja powinna zostać zastąpiona umożliwia listy operacji w oknie. Domyślna implementacja ta funkcja wywołuje [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), która zwraca DROPEFFECT_NONE domyślnie. Ponieważ ta funkcja jest wywoływana często podczas operacji przeciągania i upuszczania, powinny być zoptymalizowane możliwie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll  
 Metoda wywoływana przez platformę przed wywołaniem [ondragenter —](#ondragenter) lub [ondragover —](#ondragover) ustalenie, czy *punktu* znajduje się w regionie przewijania.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Punkty do okna kursora jest obecnie dostępna za pośrednictwem.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Zawiera lokalizacji kursora, w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt, który byłby wynikiem, jeśli podjęto zrzutu w lokalizacji określonej przez *punktu*. Może być co najmniej jeden z następujących czynności:  
  
- DROPEFFECT_NONE zrzutu będzie niedozwolone.  
  
- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
  
- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
  
- Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.  
  
- DROPEFFECT_SCROLL wskazuje, że operacji przeciągania przewijania może nastąpić lub odbywa się w elemencie docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja ta funkcja wywołuje [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), która zwraca DROPEFFECT_NONE i przewija okna, gdy kursor jest przeciągany w domyślnym regionie przewijania wewnątrz obramowania okna.  
  
##  <a name="ondrop"></a>  COleDropTarget::OnDrop  
 Wywoływane przez platformę, gdy ma wystąpić operacja przeciągania.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
*pWnd*  
 Punkty do okna kursora jest obecnie dostępna za pośrednictwem.  
  
*pDataObject*  
Wskazuje obiekt danych, który zawiera dane, które ma zostać przerwane.  
  
*dropEffect*  
Wpływ, jaki użytkownik wybrał dla operacji listy. Może być co najmniej jeden z następujących czynności:  
  
 - DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
       
 - DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
      
 - Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.  
  
*Punkt*  
Zawiera lokalizacji kursora, w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli kończy się pomyślnie; listy w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje pierwszy [ondropex —](#ondropex). Jeśli `OnDropEx` funkcji nie obsługuje listy, struktura wywołuje następnie ta funkcja elementu członkowskiego `OnDrop`. Zazwyczaj aplikacja zastępuje [ondropex —](../../mfc/reference/cview-class.md#ondropex) w klasie widoku w celu obsługi prawym przyciskiem myszy przeciągania i upuszczania. Zazwyczaj klasa widoku [OnDrop](../../mfc/reference/cview-class.md#ondrop) umożliwia obsługę prostych operacji przeciągania i upuszczania.  
  
 Domyślna implementacja klasy `COleDropTarget::OnDrop` wywołania [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), która po prostu zwraca wartość FALSE domyślnie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) w zestawie Windows SDK.  
  
##  <a name="ondropex"></a>  COleDropTarget::OnDropEx  
 Wywoływane przez platformę, gdy ma wystąpić operacja przeciągania.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Punkty do okna kursora jest obecnie dostępna za pośrednictwem.  
  
 *pDataObject*  
 Wskazuje obiekt danych, który zawiera dane, które ma zostać przerwane.  
  
 *dropDefault*  
 Wpływ, jaki użytkownik wybrał dla operacji listy domyślne na podstawie bieżącego stanu klucza. Może to być DROPEFFECT_NONE. Efekty listy zostały omówione w sekcji uwag.  
  
 *listy rozwijanej*  
 Lista efekty listy, które obsługuje miejsca źródłowego. Wartości efekt listy można łączyć, używając bitowe OR (**&#124;**) operacji. Efekty listy zostały omówione w sekcji uwag.  
  
 *Punkt*  
 Zawiera lokalizacji kursora, w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt listy, który jest wynikiem próby porzucenia w lokalizacji określonej przez *punktu*. Efekty listy zostały omówione w sekcji uwag.  
  
### <a name="remarks"></a>Uwagi  
 Struktura najpierw wywołuje tę funkcję. Jeśli nie obsługuje listy, struktura, następnie wywołuje [OnDrop](#ondrop). Zazwyczaj spowoduje przesłonięcie [ondropex —](../../mfc/reference/cview-class.md#ondropex) w klasie widoku w celu obsługi prawym przyciskiem myszy przeciągania i upuszczania. Zazwyczaj klasa widoku [OnDrop](../../mfc/reference/cview-class.md#ondrop) jest używana do obsługi wielkość liter obsługę prostych operacji przeciągania i upuszczania.  
  
 Domyślna implementacja klasy `COleDropTarget::OnDropEx` wywołania [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Domyślnie [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) po prostu zwraca wartości do wskazania [OnDrop](#ondrop) powinna być wywoływana funkcja elementu członkowskiego.  
  
 Efekty listy opisują akcję skojarzoną z operacja przeciągania. Przejrzyj następującą listę upuszczania efektów:  
  
 - DROPEFFECT_NONE zrzutu będzie niedozwolone.  
  
 - DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
  
 - DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
  
 - Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.  
  
 - DROPEFFECT_SCROLL wskazuje, że operacji przeciągania przewijania może nastąpić lub odbywa się w elemencie docelowym.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-drop) w zestawie Windows SDK.  
  
##  <a name="register"></a>  COleDropTarget::Register  
 Wywołaj tę funkcję, aby zarejestrować okna za pomocą OLE biblioteki DLL jako prawidłowe miejsca docelowego.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskazuje okna, który ma zostać zarejestrowana jako miejsca docelowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli rejestracja się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja musi być wywołana dla operacji listy do zaakceptowania.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterDragDrop](/windows/desktop/api/ole2/nf-ole2-registerdragdrop) w zestawie Windows SDK.  
  
##  <a name="revoke"></a>  COleDropTarget::Revoke  
 Wywołaj tę funkcję, zanim niszczenie dowolne okno, które zostało zarejestrowane jako miejsca docelowego za pomocą wywołania [zarejestrować](#register) go usunąć z listy miejsc docelowych.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana automatycznie z [metoda OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obsługi dla okna, który został zarejestrowany, więc zazwyczaj nie jest to konieczne jawnie wywołać tę funkcję.  
  
 Aby uzyskać więcej informacji, zobacz [RevokeDragDrop](/windows/desktop/api/ole2/nf-ole2-revokedragdrop) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC HIERSVR](../../visual-cpp-samples.md)   
 [Próbki MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDropSource](../../mfc/reference/coledropsource-class.md)
