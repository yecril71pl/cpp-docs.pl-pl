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
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367356"
---
# <a name="cmfctabdroptarget-class"></a>Klasa CMFCTabDropTarget

Zapewnia mechanizm komunikacji między formantem karty i bibliotek OLE.

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
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Wywoływane przez strukturę, gdy użytkownik przeciąga obiekt do okna karty. (Zastępuje [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Wywoływane przez platformę, gdy użytkownik przeciąga obiekt poza okno karty, który ma fokus. (Zastępuje [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Wywoływane przez platformę, gdy użytkownik przeciąga obiekt do okna karty, które ma fokus. (Zastępuje [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Wywoływane przez strukturę, gdy użytkownik zwalnia przycisk myszy na końcu operacji przeciągania. (Zastępuje [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Zarejestruj się](#register)|Rejestruje formant jako taki, który może być celem operacji przeciągania i upuszczania OLE.|

### <a name="remarks"></a>Uwagi

Ta klasa zapewnia obsługę przeciągania `CMFCBaseTabCtrl` i upuszczania dla klasy. Jeśli aplikacja inicjuje biblioteki OLE przy użyciu [afxOleInit](ole-initialization.md#afxoleinit) funkcji, `CMFCBaseTabCtrl` obiekty rejestrują się dla operacji przeciągania i upuszczania.

Klasa `CMFCTabDropTarget` rozszerza swoją klasę podstawową, tworząc kartę, która znajduje się pod kursorem, gdy operacja przeciągania występuje aktywna. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania, zobacz [Przeciąganie i upuszczanie OLE](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCTabDropTarget` obiekt i użyć jego `Register` metody.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget (Polski)](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Wywoływane przez strukturę, gdy użytkownik przeciąga obiekt do okna karty.

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
|*Pwnd*|[w] Nieużywane.|
|*pDataObject (1000)*|[w] Wskaźnik do obiektu, który przeciąga użytkownik.|
|*dwKeyState (Stan klucza)*|[w] Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.|
|*Punkt*|[w] Lokalizacja kursora we współrzędnych klienta.|

### <a name="return-value"></a>Wartość zwracana

Efekt, który powoduje, jeśli spadek występuje w miejscu określonym przez *punkt*. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda zwraca DROPEFFECT_NONE, jeśli struktura paska narzędzi nie jest w trybie dostosowywania lub format danych Schowka jest niedostępny. W przeciwnym razie zwraca `CMFCBaseTabCtrl::OnDragEnter` wynik wywołania z podanymi parametrami.

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych Schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave

Wywoływane przez platformę, gdy użytkownik przeciąga obiekt poza okno karty, który ma fokus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pwnd*|[w] Nieużywane.|

### <a name="remarks"></a>Uwagi

Ta metoda `CMFCBaseTabCtrl::OnDragLeave` wywołuje metodę, aby wykonać operację przeciągania.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDropTarget::OnDragOver

Wywoływane przez platformę, gdy użytkownik przeciąga obiekt do okna karty, które ma fokus.

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
|*Pwnd*|[w] Nieużywane.|
|*pDataObject (1000)*|[w] Wskaźnik do obiektu, który przeciąga użytkownik.|
|*dwKeyState (Stan klucza)*|[w] Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.|
|*Punkt*|[w] Położenie wskaźnika myszy we współrzędnych klienta.|

### <a name="return-value"></a>Wartość zwracana

Efekt, który powoduje, jeśli spadek występuje w miejscu określonym przez *punkt*. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda sprawia, że karta, która znajduje się pod kursorem, gdy operacja przeciągania występuje aktywne. Zwraca DROPEFFECT_NONE, jeśli struktura paska narzędzi nie jest w trybie dostosowywania lub format danych Schowka jest niedostępny. W przeciwnym razie zwraca `CMFCBaseTabCtrl::OnDragOver` wynik wywołania z podanymi parametrami.

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych Schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Wywoływane przez strukturę, gdy użytkownik zwalnia przycisk myszy na końcu operacji przeciągania.

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
|*Pwnd*|[w] Nieużywane.|
|*pDataObject (1000)*|[w] Wskaźnik do obiektu, który przeciąga użytkownik.|
|*dropEffect (efekt upuszczania)*|[w] Domyślna operacja upuszczania.|
|*lista dropList*|[w] Nieużywane.|
|*Punkt*|[w] Położenie wskaźnika myszy we współrzędnych klienta.|

### <a name="return-value"></a>Wartość zwracana

Wynikowy efekt upuszczania. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Uwagi

Ta metoda `CMFCBaseTabCtrl::OnDrop` wywołuje, jeśli struktura paska narzędzi jest w trybie dostosowywania i format danych Schowka jest dostępny. Jeśli wywołanie `CMFCBaseTabCtrl::OnDrop` zwraca wartość niezerową, ta metoda zwraca domyślny efekt upuszczania określony przez *dropEffect*. W przeciwnym razie ta metoda zwraca DROPEFFECT_NONE. Aby uzyskać więcej informacji na temat efektów upuszczania, zobacz [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Aby uzyskać więcej informacji na temat trybu dostosowywania, zobacz [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Aby uzyskać więcej informacji na temat formatów danych Schowka, zobacz [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDropTarget::Zarejestruj się

Rejestruje formant jako taki, który może być celem operacji przeciągania i upuszczania OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*p Właściciel*|[w] Formant karty, aby zarejestrować się jako miejsce docelowe upuszczania.|

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli rejestracja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) zarejestrować formant dla operacji przeciągania i upuszczania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Przeciąganie i upuszczanie elementów OLE](../../mfc/drag-and-drop-ole.md)
