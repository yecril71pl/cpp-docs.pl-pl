---
title: Klasa COleDropTarget
ms.date: 11/04/2016
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
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374994"
---
# <a name="coledroptarget-class"></a>Klasa COleDropTarget

Udostępnia mechanizm komunikacji między oknem a bibliotekami OLE.

## <a name="syntax"></a>Składnia

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|Konstruuje `COleDropTarget` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropTarget::OnDragEnter](#ondragenter)|Wywoływana, gdy kursor po raz pierwszy wchodzi do okna.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Wywoływana, gdy kursor jest przeciągany z okna.|
|[COleDropTarget::OnDragOver](#ondragover)|Wywoływana wielokrotnie, gdy kursor jest przeciągany nad oknem.|
|[COleDropTarget::OnDragscroll](#ondragscroll)|Wywoływana w celu ustalenia, czy kursor jest przeciągany do regionu przewijania okna.|
|[COleDropTarget::OnDrop](#ondrop)|Wywoływane, gdy dane są upuszczane do okna, domyślny program obsługi.|
|[COleDropTarget::OnDropEx](#ondropex)|Wywoływane, gdy dane są upuszczane do okna, początkowego programu obsługi.|
|[COleDropTarget::Zarejestruj się](#register)|Rejestruje okno jako prawidłowy obiekt docelowy upuszczania.|
|[COleDropTarget::Odwołaj](#revoke)|Powoduje, że okno przestaje być prawidłowym celem upuszczania.|

## <a name="remarks"></a>Uwagi

Tworzenie obiektu tej klasy umożliwia okno do akceptowania danych za pośrednictwem mechanizmu przeciągania i upuszczania OLE.

Aby uzyskać okno do akceptowania poleceń upuszczania, `COleDropTarget` należy najpierw utworzyć obiekt klasy, a `CWnd` następnie [wywołać](#register) Register funkcji ze wskaźnikiem do żądanego obiektu jako jedyny parametr.

Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania przy użyciu ole, zobacz artykuł [OLE przeciągania i upuszczania](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Konstruuje obiekt `COleDropTarget`klasy .

```
COleDropTarget();
```

### <a name="remarks"></a>Uwagi

Wywołanie [zarejestruj,](#register) aby skojarzyć ten obiekt z oknem.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>COleDropTarget::OnDragEnter

Wywoływana przez strukturę, gdy kursor jest przeciągany po raz pierwszy do okna.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, do które wprowadza kursor.

*pDataObject (1000)*<br/>
Wskazuje obiekt danych zawierający dane, które mogą zostać usunięte.

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Zawiera bieżącą lokalizację kursora we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem, gdyby podjęto próbę upuszczenia w lokalizacji określonej przez *punkt*. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

### <a name="remarks"></a>Uwagi

Zastąpuj tę funkcję, aby umożliwić operacje upuszczania w oknie. Domyślna implementacja wywołuje [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), który po prostu zwraca DROPEFFECT_NONE domyślnie.

Aby uzyskać więcej informacji, zobacz [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) w windows SDK.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>COleDropTarget::OnDragLeave

Wywoływana przez strukturę, gdy kursor opuszcza okno podczas operacji przeciągania.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, które kursor opuszcza.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zastąpić, jeśli chcesz zachować zachowanie specjalne, gdy operacja przeciągania opuszcza określone okno. Domyślna implementacja tej funkcji wywołuje [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Aby uzyskać więcej informacji, zobacz [IDropTarget::DragLeave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) w windows SDK.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>COleDropTarget::OnDragOver

Wywoływana przez strukturę, gdy kursor jest przeciągany przez okno.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, w które kursor jest skończny.

*pDataObject (1000)*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać usunięte.

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Zawiera bieżącą lokalizację kursora we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem, gdyby podjęto próbę upuszczenia w lokalizacji określonej przez *punkt*. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Wskazuje, że operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać zastąpiona, aby umożliwić operacje upuszczania w oknie. Domyślna implementacja tej funkcji wywołuje [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), który zwraca DROPEFFECT_NONE domyślnie. Ponieważ ta funkcja jest często wywoływana podczas operacji przeciągania i upuszczania, powinna być zoptymalizowana w miarę możliwości.

Aby uzyskać więcej informacji, zobacz [IDropTarget::Dbrawer](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>COleDropTarget::OnDragscroll

Wywoływane przez platformę przed wywołaniem [OnDragEnter](#ondragenter) lub [OnDragOver,](#ondragover) aby *ustalić,* czy punkt znajduje się w regionie przewijania.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, w które kursor jest obecnie skończą.

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Zawiera położenie kursora w pikselach względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem, gdyby podjęto próbę upuszczenia w lokalizacji określonej przez *punkt*. Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Wskazuje, że operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

### <a name="remarks"></a>Uwagi

Zastądnie tej funkcji, jeśli chcesz zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja tej funkcji wywołuje [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), który zwraca DROPEFFECT_NONE i przewija okno, gdy kursor jest przeciągany do domyślnego regionu przewijania wewnątrz obramowania okna.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDropTarget::OnDrop

Wywoływana przez platformę, gdy ma wystąpić operacja upuszczania.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, w które kursor jest obecnie skończą.

*pDataObject (1000)*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać usunięte.

*dropEffect (efekt upuszczania)*<br/>
Efekt, który użytkownik wybrał dla operacji upuszczania. Może to być co najmniej jeden z następujących:

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

*Punkt*<br/>
Zawiera położenie kursora w pikselach względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli spadek zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ramy po raz pierwszy wywołuje [OnDropEx](#ondropex). Jeśli `OnDropEx` funkcja nie obsługuje drop, framework następnie wywołuje `OnDrop`tę funkcję elementu członkowskiego, . Zazwyczaj aplikacja zastępuje [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie view do obsługi prawego przycisku myszy przeciągania i upuszczania. Zazwyczaj klasa widoku [OnDrop](../../mfc/reference/cview-class.md#ondrop) służy do obsługi prostego przeciągania i upuszczania.

Domyślna implementacja wywołań `COleDropTarget::OnDrop` [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), która domyślnie zwraca FALSE.

Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) w windows SDK.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDropTarget::OnDropEx

Wywoływana przez platformę, gdy ma wystąpić operacja upuszczania.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, w które kursor jest obecnie skończą.

*pDataObject (1000)*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać usunięte.

*dropDefault (niem.*<br/>
Efekt, który użytkownik wybrał dla domyślnej operacji upuszczania na podstawie bieżącego stanu klucza. Można go DROPEFFECT_NONE. Efekty upuszczania są omówione w sekcji Uwagi.

*lista dropList*<br/>
Lista efektów upuszczania, które obsługuje źródło upuszczania. Wartości efektu upuszczania można łączyć za pomocą operacji bitowej OR** (&#124;). ** Efekty upuszczania są omówione w sekcji Uwagi.

*Punkt*<br/>
Zawiera położenie kursora w pikselach względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania wynikający z próby upuszczania w lokalizacji określonej przez *punkt*. Efekty upuszczania są omówione w sekcji Uwagi.

### <a name="remarks"></a>Uwagi

Struktura najpierw wywołuje tę funkcję. Jeśli nie obsługuje drop, framework następnie wywołuje [OnDrop](#ondrop). Zazwyczaj można zastąpić [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie widoku do obsługi prawego przycisku myszy przeciągania i upuszczania. Zazwyczaj view class [OnDrop](../../mfc/reference/cview-class.md#ondrop) jest używany do obsługi przypadku obsługi prostych przeciągania i upuszczania.

Domyślna implementacja wywołań `COleDropTarget::OnDropEx` [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Domyślnie [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) po prostu zwraca wartość manekina, aby wskazać [OnDrop](#ondrop) funkcji elementu członkowskiego powinny być wywoływane.

Efekty upuszczania opisują akcję skojarzoną z operacją upuszczania. Zobacz następującą listę efektów upuszczania:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Wskazuje, że operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

Aby uzyskać więcej informacji, zobacz [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) w windows SDK.

## <a name="coledroptargetregister"></a><a name="register"></a>COleDropTarget::Zarejestruj się

Wywołanie tej funkcji, aby zarejestrować okno z bibliotekami DLL OLE jako prawidłowy cel upuszczania.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, które ma być zarejestrowane jako miejsce docelowe upuszczania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli rejestracja zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja musi być wywołana dla operacji upuszczania, które mają być akceptowane.

Aby uzyskać więcej informacji, zobacz [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) w windows SDK.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDropTarget::Odwołaj

Wywołanie tej funkcji przed zniszczeniem dowolnego okna, które zostało zarejestrowane jako miejsce docelowe upuszczania za pośrednictwem wywołania [zarejestruj się,](#register) aby usunąć go z listy celów upuszczania.

```
virtual void Revoke();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana automatycznie z [onDestroy](../../mfc/reference/cwnd-class.md#ondestroy) obsługi dla okna, które zostało zarejestrowane, więc zwykle nie jest konieczne, aby wywołać tę funkcję jawnie.

Aby uzyskać więcej informacji, zobacz [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDropSource](../../mfc/reference/coledropsource-class.md)
