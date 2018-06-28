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
ms.openlocfilehash: fec20d8bb960d48392f2d174dab9ee6497738c80
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039605"
---
# <a name="coledroptarget-class"></a>Klasa COleDropTarget
Udostępnia mechanizm komunikacji między okna i bibliotek OLE.  
  
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
|[COleDropTarget::OnDragEnter](#ondragenter)|Wywoływane, gdy kursor po raz pierwszy najedzie okna.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Wywoływane, gdy kursor jest przeciągany poza okna.|  
|[COleDropTarget::OnDragOver](#ondragover)|Wywołuje się wielokrotnie, gdy kursor jest przeciągany nad oknem.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Wywołuje się, by określić czy kursor jest przeciągany w regionie przewijania okna.|  
|[COleDropTarget::OnDrop](#ondrop)|Wywoływane, gdy dane są przenoszone do okna, domyślny program obsługi.|  
|[COleDropTarget::OnDropEx](#ondropex)|Wywoływane, gdy dane są przenoszone do okna obsługi początkowej.|  
|[COleDropTarget::Register](#register)|Okno rejestrów jako prawidłowy miejsca docelowego.|  
|[COleDropTarget::Revoke](#revoke)|Powoduje, że okno, aby zaprzestać jest prawidłowy miejsca docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Tworzenie obiektu ta klasa umożliwia okno, aby akceptować dane za pomocą mechanizmu przeciąganie i upuszczanie OLE.  
  
 Aby uzyskać okno, aby zaakceptować poleceń drop, należy najpierw utworzyć obiektu `COleDropTarget` klasy, a następnie wywołać [zarejestrować](#register) funkcji za pomocą wskaźnika do żądaną `CWnd` obiektu jako parametr tylko.  
  
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
 Wywołanie [zarejestrować](#register) Aby powiązać ten obiekt z okna.  
  
##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter  
 Wywoływane przez platformę, gdy kursor najpierw zostanie przeciągnięty do okna.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wprowadza punktów do okna kursora.  
  
 *Obiekt pDataObject*  
 Wskazuje na obiekt danych zawierające dane, które można było porzucić.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, i **MK_RBUTTON**.  
  
 *Punkt*  
 Zawiera bieżącą lokalizację kursora we współrzędnych klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wpływ, jaki sytuacji, gdy spadek podjęto w lokalizacji określonej przez *punktu*. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE` Spadek będzie niemożliwe.  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
- `DROPEFFECT_SCROLL` Operację przeciągania przewijania może nastąpić lub występuje w miejscu docelowym.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby umożliwić operacji listy w oknie. Domyślna implementacja wywołuje [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), która zwraca po prostu `DROPEFFECT_NONE` domyślnie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) w zestawie Windows SDK.  
  
##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave  
 Wywoływane przez platformę, gdy kursor opuszcza okna podczas przeciągania operacji jest włączona.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Opuszcza punktów do okna kursora.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, jeśli mają specjalnego zachowania, gdy operacja przeciągania pozostawia określone okno. Domyślna implementacja ta funkcja wymaga [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) w zestawie Windows SDK.  
  
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
 Punkty do okna, nad którym znajduje się kursor.  
  
 *Obiekt pDataObject*  
 Wskazuje na obiekt danych, który zawiera dane, które ma być przerwane.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, i **MK_RBUTTON**.  
  
 *Punkt*  
 Zawiera bieżącą lokalizację kursora we współrzędnych klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wpływ, jaki sytuacji, gdy spadek podjęto w lokalizacji określonej przez *punktu*. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE` Spadek będzie niemożliwe.  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
- `DROPEFFECT_SCROLL` Wskazuje, że operacja przewijania przeciągania może nastąpić, lub jest wykonywana w celu.  
  
### <a name="remarks"></a>Uwagi  
 Aby umożliwić operacji listy w oknie powinna zostać zastąpiona tej funkcji. Domyślna implementacja ta funkcja wymaga [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), która zwraca `DROPEFFECT_NONE` domyślnie. Ponieważ ta funkcja jest wywoływana często podczas operacji przeciągania i upuszczania, powinien być zoptymalizowany możliwie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll  
 Metoda wywoływana przez platformę przed wywołaniem [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) ustalenie, czy *punktu* znajduje się w regionie przewijania.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Punkty do okna, gdy kursor jest aktualnie za pośrednictwem.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, i **MK_RBUTTON**.  
  
 *Punkt*  
 Zawiera lokalizację kursor w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wpływ, jaki sytuacji, gdy spadek podjęto w lokalizacji określonej przez *punktu*. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE` Spadek będzie niemożliwe.  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
- `DROPEFFECT_SCROLL` Wskazuje, że operacja przewijania przeciągania może nastąpić, lub jest wykonywana w celu.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, gdy chcesz zapewnić specjalnego zachowania dla tego zdarzenia. Domyślna implementacja ta funkcja wymaga [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), która zwraca `DROPEFFECT_NONE` i przewija okna, gdy kursor jest przeciągany do domyślnego regionu przewijania wewnątrz obramowania okna.  
  
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
 Punkty do okna, gdy kursor jest aktualnie za pośrednictwem.  
  
 *Obiekt pDataObject*  
 Wskazuje na obiekt danych, który zawiera dane, które ma być przerwane.  
  
 *dropEffect*  
 Wpływ, jaki użytkownik wybrał dla operacji usuwania. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
 *Punkt*  
 Zawiera lokalizację kursor w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli listy zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze wywołania framework [OnDropEx](#ondropex). Jeśli `OnDropEx` funkcji nie obsługuje usuwania, struktura następnie wywołuje funkcji członkowskiej, `OnDrop`. Zwykle aplikacja zastępuje [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie widoku do obsługi prawego przycisku myszy przeciągania i upuszczania. Zazwyczaj klasa widoku [OnDrop](../../mfc/reference/cview-class.md#ondrop) umożliwia obsługę prostych operacji przeciągania i upuszczania.  
  
 Domyślna implementacja `COleDropTarget::OnDrop` wywołania [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), która zwraca po prostu **FALSE** domyślnie.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) w zestawie Windows SDK.  
  
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
 Punkty do okna, gdy kursor jest aktualnie za pośrednictwem.  
  
 *Obiekt pDataObject*  
 Wskazuje na obiekt danych, który zawiera dane, które ma być przerwane.  
  
 *dropDefault*  
 Wpływ, jaki użytkownik wybrał dla operacji upuszczania domyślne na podstawie bieżącego stanu klucza. Można ją `DROPEFFECT_NONE`. Efekty upuszczania omówiono w sekcji uwag.  
  
 *listy rozwijanej*  
 Lista efekty upuszczania, które obsługuje miejsca źródłowego. Wartości efekt listy można łączyć, używając wartości bitowe lub ( **&#124;**) operacji. Efekty upuszczania omówiono w sekcji uwag.  
  
 *Punkt*  
 Zawiera lokalizację kursor w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt upuszczania, który jest wynikiem próby porzucenia w lokalizacji określonej przez *punktu*. Efekty upuszczania omówiono w sekcji uwag.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje najpierw tej funkcji. Jeśli nie obsługuje usuwania, struktura następnie wywołuje [OnDrop](#ondrop). Zazwyczaj spowoduje zastąpienie [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie widoku do obsługi prawego przycisku myszy przeciągania i upuszczania. Zazwyczaj klasa widoku [OnDrop](../../mfc/reference/cview-class.md#ondrop) służy do obsługi w przypadku obsługę prostych operacji przeciągania i upuszczania.  
  
 Domyślna implementacja `COleDropTarget::OnDropEx` wywołania [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Domyślnie [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) po prostu zwraca wartość fikcyjny [OnDrop](#ondrop) powinna być wywoływana funkcja elementu członkowskiego.  
  
 Efekty upuszczania opisują akcję skojarzoną z operacji usuwania. Lista poniższych upuszczania efekty:  
  
- `DROPEFFECT_NONE` Spadek będzie niemożliwe.  
  
- `DROPEFFECT_COPY` Czy można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE` Czy można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK` Czy można ustanowić łącze z porzuconych danych do oryginalnych danych.  
  
- `DROPEFFECT_SCROLL` Wskazuje, że operacja przewijania przeciągania może nastąpić, lub jest wykonywana w celu.  
  
 Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) w zestawie Windows SDK.  
  
##  <a name="register"></a>  COleDropTarget::Register  
 Wywołanie tej funkcji można zarejestrować okna w OLE bibliotek DLL jako prawidłowy miejsca docelowego.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Punkty do okna, które ma zostać zarejestrowany jako miejsca docelowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli rejestracja zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja musi być wywołana dla operacji listy mają być akceptowane.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) w zestawie Windows SDK.  
  
##  <a name="revoke"></a>  COleDropTarget::Revoke  
 Wywołanie tej funkcji przed niszczenie dowolnym oknie, który został zarejestrowany jako miejsca docelowego poprzez wywołanie [zarejestrować](#register) go usunąć z listy miejsc docelowych.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana automatycznie z [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obsługi dla elementu typu window, który został zarejestrowany, dlatego zazwyczaj nie jest konieczne jawnie wywołanie tej funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDropSource](../../mfc/reference/coledropsource-class.md)
