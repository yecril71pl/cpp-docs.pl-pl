---
title: Klasa CMFCTabDropTarget
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
ms.openlocfilehash: 9160cfd847977f98ac22eecd72632822c751a3aa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834235"
---
# <a name="cmfctabdroptarget-class"></a>Klasa CMFCTabDropTarget

Zapewnia mechanizm komunikacji między kontrolką karty i bibliotekami OLE.

## <a name="syntax"></a>Składnia

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Wywoływane przez platformę, gdy użytkownik przeciąga obiekt w oknie karty. (Przesłania [COleDropTarget:: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Wywoływane przez platformę, gdy użytkownik przeciągnie obiekt poza oknem karty, które ma fokus. (Przesłania [COleDropTarget:: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Wywoływane przez platformę, gdy użytkownik przeciąga obiekt do okna karty, które ma fokus. (Przesłania [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy na końcu operacji przeciągania. (Przesłania [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget:: register](#register)|Rejestruje formant jako jeden, który może być obiektem docelowym operacji przeciągania i upuszczania OLE.|

### <a name="remarks"></a>Uwagi

Ta klasa zapewnia obsługę przeciągania i upuszczania `CMFCBaseTabCtrl` klasy. Jeśli aplikacja inicjuje biblioteki OLE przy użyciu funkcji [AfxOleInit](ole-initialization.md#afxoleinit) , `CMFCBaseTabCtrl` obiekty są rejestrowane dla operacji przeciągania i upuszczania.

`CMFCTabDropTarget`Klasa rozszerza swoją klasę bazową, ustawiając kartę znajdującą się pod kursorem, gdy operacja przeciągania stanie się aktywna. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz [OLE przeciąganie i upuszczanie](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCTabDropTarget` obiektu i używania jego `Register` metody.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbasetabctrl. h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a> CMFCTabDropTarget::OnDragEnter

Wywoływane przez platformę, gdy użytkownik przeciąga obiekt w oknie karty.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Przestrzeń.

*pDataObject*\
podczas Wskaźnik do obiektu przeciąganego przez użytkownika.

*dwKeyState*\
podczas Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*\
podczas Lokalizacja kursora we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który powstaje, gdy porzucanie występuje w lokalizacji określonej przez *punkt*. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda zwraca DROPEFFECT_NONE, jeśli struktura paska narzędzi nie jest w trybie dostosowywania lub nie jest dostępny format danych Schowka. W przeciwnym razie zwraca wynik wywołania `CMFCBaseTabCtrl::OnDragEnter` z podanymi parametrami.

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar:: Isdostosowywaniemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a> CMFCTabDropTarget::OnDragLeave

Wywoływane przez platformę, gdy użytkownik przeciągnie obiekt poza oknem karty, które ma fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Przestrzeń.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje `CMFCBaseTabCtrl::OnDragLeave` metodę w celu wykonania operacji przeciągania.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a> CMFCTabDropTarget::OnDragOver

Wywoływane przez platformę, gdy użytkownik przeciąga obiekt do okna karty, które ma fokus.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Przestrzeń.

*pDataObject*\
podczas Wskaźnik do obiektu przeciąganego przez użytkownika.

*dwKeyState*\
podczas Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*\
podczas Położenie wskaźnika myszy w współrzędnej klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który powstaje, gdy porzucanie występuje w lokalizacji określonej przez *punkt*. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda sprawia, że karta znajduje się pod kursorem, gdy operacja przeciągania stanie się aktywna. Zwraca DROPEFFECT_NONE, jeśli struktura paska narzędzi nie jest w trybie dostosowywania lub nie jest dostępny format danych Schowka. W przeciwnym razie zwraca wynik wywołania `CMFCBaseTabCtrl::OnDragOver` z podanymi parametrami.

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar:: Isdostosowywaniemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a> CMFCTabDropTarget::OnDropEx

Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy na końcu operacji przeciągania.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*\
podczas Przestrzeń.

*pDataObject*\
podczas Wskaźnik do obiektu przeciąganego przez użytkownika.

*dropEffect*\
podczas Domyślna operacja upuszczania.

*dropList*\
podczas Przestrzeń.

*moment*\
podczas Położenie wskaźnika myszy w współrzędnej klienta.

### <a name="return-value"></a>Wartość zwracana

Wynikowy efekt upuszczania. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje, `CMFCBaseTabCtrl::OnDrop` czy struktura paska narzędzi jest w trybie dostosowywania i czy jest dostępny format danych Schowka. Jeśli wywołanie `CMFCBaseTabCtrl::OnDrop` zwraca wartość różną od zera, ta metoda zwraca domyślny efekt upuszczania określony przez *DROPEFFECT*. W przeciwnym razie ta metoda zwraca DROPEFFECT_NONE. Aby uzyskać więcej informacji na temat efektów upuszczania, zobacz [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar:: Isdostosowywaniemode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych schowka, zobacz [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a> CMFCTabDropTarget:: register

Rejestruje formant jako jeden, który może być obiektem docelowym operacji przeciągania i upuszczania OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

*pOwner*\
podczas Kontrolka karta, która ma zostać zarejestrowana jako element docelowy upuszczania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli rejestracja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [COleDropTarget:: Register](../../mfc/reference/coledroptarget-class.md#register) w celu zarejestrowania kontroli dla operacji przeciągania i upuszczania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Przeciąganie i upuszczanie elementów OLE](../../mfc/drag-and-drop-ole.md)
