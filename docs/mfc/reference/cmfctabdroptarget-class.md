---
title: Klasa CMFCTabDropTarget | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs: C++
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ff17f7312f5e04b6ae900e792523155705a3b4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctabdroptarget-class"></a>Klasa CMFCTabDropTarget
Udostępnia mechanizm komunikacji między formantem karty i bibliotek OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|Domyślny konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|Nazwa|Opis|  
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Wywoływane przez platformę, gdy użytkownik przeciąga obiektu w oknie kartę. (Przesłania [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Wywoływane przez platformę, gdy użytkownik przeciąga obiektu poza oknem kartę, który ma fokus. (Przesłania [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Wywoływane przez platformę, gdy użytkownik przeciąga obiektu na okno karty, który ma fokus. (Przesłania [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy w końcu operacja przeciągania. (Przesłania [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|  
|[CMFCTabDropTarget::Register](#register)|Rejestruje, jaką może być elementem docelowym operacji przeciągania i upuszczania OLE.|  
  
### <a name="remarks"></a>Uwagi  
 Ta klasa umożliwia obsługę przeciągania i upuszczania `CMFCBaseTabCtrl` klasy. Jeśli aplikacja jest inicjowana przy użyciu bibliotek OLE [afxoleinit —](ole-initialization.md#afxoleinit) funkcji `CMFCBaseTabCtrl` obiektów rejestrują się dla operacji przeciągania i upuszczania.  
  
 `CMFCTabDropTarget` Klasa rozszerza swojej klasy podstawowej, wprowadzając karcie podczas operacji przeciągania active jest pod kursorem. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCTabDropTarget` obiektu i używać jej `Register` metody.  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxbasetabctrl.h  
  
##  <a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter  
 Wywoływane przez platformę, gdy użytkownik przeciąga obiektu w oknie kartę.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWnd`|Nieużywane.|  
|[in]`pDataObject`|Wskaźnik do obiektu, którą przeciąga użytkownik.|  
|[in]`dwKeyState`|Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, i `MK_RBUTTON`.|  
|[in]`point`|Lokalizacja kursora we współrzędnych klienta.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt, który powoduje spadek występuje w lokalizacji określonej przez `point`. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `DROPEFFECT_NONE` framework paska narzędzi nie jest w trybie dostosowywania lub formatu danych Schowka jest niedostępny. W przeciwnym razie zwraca wartość wyniku wywołania metody `CMFCBaseTabCtrl::OnDragEnter` z podanych parametrów.  
  
 Aby uzyskać więcej informacji dotyczących trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave  
 Wywoływane przez platformę, gdy użytkownik przeciąga obiektu poza oknem kartę, który ma fokus.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWnd`|Nieużywane.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje `CMFCBaseTabCtrl::OnDragLeave` metody do wykonania tej operacji przeciągania.  
  
##  <a name="ondragover"></a>CMFCTabDropTarget::OnDragOver  
 Wywoływane przez platformę, gdy użytkownik przeciąga obiektu na okno karty, który ma fokus.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWnd`|Nieużywane.|  
|[in]`pDataObject`|Wskaźnik do obiektu, którą przeciąga użytkownik.|  
|[in]`dwKeyState`|Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, i `MK_RBUTTON`.|  
|[in]`point`|Lokalizacja wskaźnika myszy we współrzędnych klienta.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt, który powoduje spadek występuje w lokalizacji określonej przez `point`. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że karcie podczas operacji przeciągania active jest pod kursorem. Zwraca `DROPEFFECT_NONE` framework paska narzędzi nie jest w trybie dostosowywania lub formatu danych Schowka jest niedostępny. W przeciwnym razie zwraca wartość wyniku wywołania metody `CMFCBaseTabCtrl::OnDragOver` z podanych parametrów.  
  
 Aby uzyskać więcej informacji dotyczących trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx  
 Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy w końcu operacja przeciągania.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pWnd`|Nieużywane.|  
|[in]`pDataObject`|Wskaźnik do obiektu, którą przeciąga użytkownik.|  
|[in]`dropEffect`|Operacja jej porzucenia domyślne.|  
|[in]`dropList`|Nieużywane.|  
|[in]`point`|Lokalizacja wskaźnika myszy we współrzędnych klienta.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Skutek upuszczania. Można co najmniej jeden z następujących czynności:  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje `CMFCBaseTabCtrl::OnDrop` Jeśli framework paska narzędzi w trybie dostosowania i formatu danych Schowka jest dostępny. Jeśli wywołanie `CMFCBaseTabCtrl::OnDrop` zwraca wartość różną od zera, ta metoda zwraca domyślny efekt upuszczania określony przez `dropEffect`. W przeciwnym razie ta metoda zwraca `DROPEFFECT_NONE`. Aby uzyskać więcej informacji o skutki upuszczania, zobacz [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).  
  
 Aby uzyskać więcej informacji dotyczących trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="register"></a>CMFCTabDropTarget::Register  
 Rejestruje, jaką może być elementem docelowym operacji przeciągania i upuszczania OLE.  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pOwner`|Formantu karty, aby zarejestrować jako miejsca docelowego.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli rejestracja powiodła się. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) zarejestrować formant dla operacji przeciągania i upuszczania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md)



