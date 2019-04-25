---
title: CMFCTabDropTarget Class
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 8b24d7679edfaab4d4eeb6d59770f30cd4253580
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252987"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget Class

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
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Wywoływane przez platformę, gdy użytkownik przeciągnie obiektu do okna karty. (Przesłania [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Wywoływane przez platformę, gdy użytkownik przeciągnie obiekt poza oknem karty, który ma fokus. (Przesłania [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Wywoływane przez platformę, gdy użytkownik przeciągnie obiektu na okno karty, który ma fokus. (Przesłania [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy po zakończeniu operacji przeciągania. (Przesłania [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Register](#register)|Rejestruje formantu jako taki, który może być celem operacji przeciągania i upuszczania OLE.|

### <a name="remarks"></a>Uwagi

Ta klasa umożliwia przeciąganie i upuszczanie `CMFCBaseTabCtrl` klasy. Jeśli aplikacja inicjuje bibliotek OLE przy użyciu [afxoleinit —](ole-initialization.md#afxoleinit) funkcji `CMFCBaseTabCtrl` obiektów rejestrować się w przypadku operacji przeciągania i upuszczania.

`CMFCTabDropTarget` Klasa rozszerza swojej klasy bazowej, wprowadzając kartę która podczas operacji przeciągania active jest pod kursorem. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCTabDropTarget` obiektu i używać jej `Register` metody.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Wymagania

**Header:** afxbasetabctrl.h

##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter

Wywoływane przez platformę, gdy użytkownik przeciągnie obiektu do okna karty.

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
|*pWnd*|[in] Nieużywane.|
|*pDataObject*|[in] Wskaźnik do obiektu, który użytkownik przeciąga.|
|*dwKeyState*|[in] Zawiera stan klawisze modyfikujące. Jest to kombinacja którakolwiek z następujących czynności: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.|
|*Punkt*|[in] Lokalizacja kursora w współrzędne klienta.|

### <a name="return-value"></a>Wartość zwracana

Wpływ, jaki wyniki, jeśli listy występuje w lokalizacji określonej przez *punktu*. Może być co najmniej jeden z następujących czynności:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda zwraca DROPEFFECT_NONE, jeśli struktura paska narzędzi nie jest w trybie dostosowywania lub formatu danych Schowka jest niedostępny. W przeciwnym razie zwraca wartość wyniku wywołania metody `CMFCBaseTabCtrl::OnDragEnter` przy użyciu podanych parametrów.

Aby uzyskać więcej informacji na temat trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave

Wywoływane przez platformę, gdy użytkownik przeciągnie obiekt poza oknem karty, który ma fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pWnd*|[in] Nieużywane.|

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `CMFCBaseTabCtrl::OnDragLeave` metody do wykonania tej operacji przeciągania.

##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver

Wywoływane przez platformę, gdy użytkownik przeciągnie obiektu na okno karty, który ma fokus.

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
|*pWnd*|[in] Nieużywane.|
|*pDataObject*|[in] Wskaźnik do obiektu, który użytkownik przeciąga.|
|*dwKeyState*|[in] Zawiera stan klawisze modyfikujące. Jest to kombinacja którakolwiek z następujących czynności: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.|
|*Punkt*|[in] Lokalizacja wskaźnik myszy na współrzędne klienta.|

### <a name="return-value"></a>Wartość zwracana

Wpływ, jaki wyniki, jeśli listy występuje w lokalizacji określonej przez *punktu*. Może być co najmniej jeden z następujących czynności:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda powoduje, że karta, która jest pod kursorem w przypadku aktywnych operacji przeciągania. Zwraca DROPEFFECT_NONE, jeśli w ramach narzędzi nie jest w trybie dostosowywania lub formatu danych Schowka jest niedostępny. W przeciwnym razie zwraca wartość wyniku wywołania metody `CMFCBaseTabCtrl::OnDragOver` przy użyciu podanych parametrów.

Aby uzyskać więcej informacji na temat trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx

Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy po zakończeniu operacji przeciągania.

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
|*pWnd*|[in] Nieużywane.|
|*pDataObject*|[in] Wskaźnik do obiektu, który użytkownik przeciąga.|
|*dropEffect*|[in] Limit czasu operacji listy domyślne.|
|*listy rozwijanej*|[in] Nieużywane.|
|*Punkt*|[in] Lokalizacja wskaźnik myszy na współrzędne klienta.|

### <a name="return-value"></a>Wartość zwracana

Ostateczny wynik listy. Może być co najmniej jeden z następujących czynności:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `CMFCBaseTabCtrl::OnDrop` Jeśli framework narzędzi jest w trybie dostosowywania i formatu danych Schowka jest dostępna. Jeśli wywołanie `CMFCBaseTabCtrl::OnDrop` zwraca wartość różną od zera, ta metoda zwraca domyślny efekt listy określonego przez *dropEffect*. W przeciwnym razie metoda ta zwraca DROPEFFECT_NONE. Aby uzyskać więcej informacji na temat skutków listy zobacz [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Aby uzyskać więcej informacji na temat trybu dostosowania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

##  <a name="register"></a>  CMFCTabDropTarget::Register

Rejestruje formantu jako taki, który może być celem operacji przeciągania i upuszczania OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pOwner*|[in] Kontrolka karty, aby zarejestrować się jako miejsca docelowego.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli rejestracja powiodła się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) do rejestrowania formantu dla operacji przeciągania i upuszczania.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md)
