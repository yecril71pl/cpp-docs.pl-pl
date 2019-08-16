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
ms.openlocfilehash: 891b19112c8baf2efb088f064892e1ea19a7deab
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503978"
---
# <a name="coledroptarget-class"></a>Klasa COleDropTarget

Zapewnia mechanizm komunikacji między oknem a bibliotekami OLE.

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
|[COleDropTarget::OnDragEnter](#ondragenter)|Wywołuje się, gdy kursor po raz pierwszy przejdzie do okna.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Wywołuje się, gdy kursor jest przeciągany z okna.|
|[COleDropTarget::OnDragOver](#ondragover)|Wywoływana wielokrotnie, gdy kursor jest przeciągany nad oknem.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Wywołuje się, by określić, czy kursor jest przeciągany do regionu przewijania okna.|
|[COleDropTarget::OnDrop](#ondrop)|Wywoływana, gdy dane zostaną usunięte do okna, domyślna procedura obsługi.|
|[COleDropTarget::OnDropEx](#ondropex)|Wywoływana, gdy dane zostaną usunięte do okna, początkowa procedura obsługi.|
|[COleDropTarget:: register](#register)|Rejestruje okno jako prawidłowy element docelowy upuszczania.|
|[COleDropTarget:: odwołaj](#revoke)|Powoduje, że okno przestaje być prawidłowym miejscem docelowym upuszczania.|

## <a name="remarks"></a>Uwagi

Utworzenie obiektu tej klasy pozwala okna akceptującego dane za pomocą mechanizmu przeciągania i upuszczania OLE.

Aby uzyskać okno akceptujące polecenia DROP, należy najpierw utworzyć obiekt `COleDropTarget` klasy, a następnie wywołać funkcję [register](#register) ze wskaźnikiem do żądanego `CWnd` obiektu jako jedynego parametru.

Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą technologii OLE, zobacz artykuł przeciąganie [i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Konstruuje obiekt klasy `COleDropTarget`.

```
COleDropTarget();
```

### <a name="remarks"></a>Uwagi

Wywołaj [Rejestr](#register) , aby skojarzyć ten obiekt z oknem.

##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter

Wywoływane przez platformę po pierwszym przeciągnięciu kursora do okna.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje przedział czasu wprowadzania kursora.

*pDataObject*<br/>
Wskazuje obiekt danych zawierający dane, które można porzucić.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Zawiera bieżącą lokalizację kursora we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem próby porzucenia w lokalizacji określonej przez *punkt*. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE nie jest dozwolone.

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

- DROPEFFECT_SCROLL operację przewijania przeciągnij lub występuje w elemencie docelowym.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby zezwolić na wykonywanie operacji upuszczania w oknie. Domyślne wywołania implementacji [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), które po prostu domyślnie zwracają DROPEFFECT_NONE.

Aby uzyskać więcej informacji, zobacz [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) w Windows SDK.

##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave

Wywoływane przez platformę, gdy kursor opuszcza okno, gdy działa operacja przeciągania.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, w którym znajduje się kursor.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, jeśli chcesz mieć specjalne zachowanie, gdy operacja przeciągania opuści określone okno. Domyślna implementacja tej funkcji wywołuje [CView:: OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Aby uzyskać więcej informacji, zobacz [IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) w Windows SDK.

##  <a name="ondragover"></a>COleDropTarget::OnDragOver

Wywoływane przez platformę, gdy kursor jest przeciągany nad oknem.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, nad którym znajduje się kursor.

*pDataObject*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać porzucone.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Zawiera bieżącą lokalizację kursora we współrzędnych klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem próby porzucenia w lokalizacji określonej przez *punkt*. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE nie jest dozwolone.

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągnij ma miejsce lub występuje w elemencie docelowym.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna zostać przesłonięta, aby zezwalać na operacje upuszczania w oknie. Domyślna implementacja tej funkcji wywołuje [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover), która domyślnie zwraca DROPEFFECT_NONE. Ponieważ ta funkcja jest wywoływana często podczas operacji przeciągania i upuszczania, powinna być zoptymalizowana możliwie największej ilości.

Aby uzyskać więcej informacji, zobacz [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll

Wywoływane przez platformę przed wywołaniem metody [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) w celu określenia, czy *punkt* znajduje się w regionie przewijania.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje przedział czasu, w którym znajduje się kursor.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Zawiera lokalizację kursora (w pikselach) względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Efekt, który byłby wynikiem próby porzucenia w lokalizacji określonej przez *punkt*. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE nie jest dozwolone.

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągnij ma miejsce lub występuje w elemencie docelowym.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, jeśli chcesz zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja tej funkcji wywołuje [CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), która zwraca DROPEFFECT_NONE i przewija okno po przeciągnięciu kursora do domyślnego regionu przewijania wewnątrz obramowania okna.

##  <a name="ondrop"></a>COleDropTarget:: OnDrop

Wywoływane przez platformę, gdy operacja upuszczania ma zostać wykonana.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje przedział czasu, w którym znajduje się kursor.

*pDataObject*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać porzucone.

*dropEffect*<br/>
Wpływ, jaki użytkownik wybrał dla operacji drop. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

*moment*<br/>
Zawiera lokalizację kursora (w pikselach) względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli porzucanie powiodło się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Platforma najpierw wywołuje [OnDropEx](#ondropex). Jeśli funkcja nie obsługuje upuszczania, struktura następnie wywołuje tę `OnDrop`funkcję elementu członkowskiego. `OnDropEx` Zwykle aplikacja przesłania [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie widoku, aby obsłużyć przycisk myszy, przeciągnij i upuść. Zazwyczaj Klasa widoku jest używana [](../../mfc/reference/cview-class.md#ondrop) do obsługi prostego przeciągania i upuszczania.

Domyślna implementacja `COleDropTarget::OnDrop` wywołań [CView:: OnDrop](../../mfc/reference/cview-class.md#ondrop), która po prostu zwraca wartość false.

Aby uzyskać więcej informacji, zobacz [IDropTarget::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) w Windows SDK.

##  <a name="ondropex"></a>COleDropTarget::OnDropEx

Wywoływane przez platformę, gdy operacja upuszczania ma zostać wykonana.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje przedział czasu, w którym znajduje się kursor.

*pDataObject*<br/>
Wskazuje obiekt danych, który zawiera dane, które mają zostać porzucone.

*dropDefault*<br/>
Efekt wybrany przez użytkownika dla domyślnej operacji upuszczania na podstawie bieżącego stanu klucza. Może być DROPEFFECT_NONE. Efekty upuszczania zostały omówione w sekcji uwagi.

*dropList*<br/>
Lista efektów upuszczania obsługiwanych przez źródło upuszczania. Wartości efektów upuszczania można łączyć za pomocą operacji bitowej lub ( **&#124;** ). Efekty upuszczania zostały omówione w sekcji uwagi.

*moment*<br/>
Zawiera lokalizację kursora (w pikselach) względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania spowodowany próbą porzucenia w lokalizacji określonej przez *punkt*. Efekty upuszczania zostały omówione w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Platforma najpierw wywołuje tę funkcję. Jeśli nie obsługuje upuszczania, struktura następnie wywołuje metodę OnDrop. [](#ondrop) Zwykle przesłonisz [OnDropEx](../../mfc/reference/cview-class.md#ondropex) w klasie widoku, aby obsługiwały prawy przycisk myszy, przeciągnij i upuść. Zazwyczaj Klasa widoku jest używana [](../../mfc/reference/cview-class.md#ondrop) do obsługi wielkości liter dla prostego przeciągania i upuszczania.

Domyślna implementacja `COleDropTarget::OnDropEx` wywołań [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex). Domyślnie [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex) po prostu zwraca wartość fikcyjną, aby wskazać, [](#ondrop) że funkcja elementu członkowskiego OnDrop powinna być wywoływana.

Efekty upuszczania opisują akcję skojarzoną z operacją drop. Zobacz poniższą listę efektów upuszczania:

- DROPEFFECT_NONE nie jest dozwolone.

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągnij ma miejsce lub występuje w elemencie docelowym.

Aby uzyskać więcej informacji, zobacz [IDropTarget::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) w Windows SDK.

##  <a name="register"></a>COleDropTarget:: register

Wywołaj tę funkcję, aby zarejestrować okno z biblioteką DLL OLE jako prawidłowym elementem docelowym upuszczania.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, które ma zostać zarejestrowane jako element docelowy upuszczania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli rejestracja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja musi być wywołana dla operacji upuszczania do zaakceptowania.

Aby uzyskać więcej informacji, zobacz [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) w Windows SDK.

##  <a name="revoke"></a>COleDropTarget:: odwołaj

Wywołaj tę funkcję przed zniszczeniem dowolnego okna, które zostało zarejestrowane jako element docelowy upuszczania za pośrednictwem wywołania do [rejestracji](#register) w celu usunięcia go z listy obiektów docelowych upuszczania.

```
virtual void Revoke();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana automatycznie z procedury [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) dla zarejestrowanego okna, więc zazwyczaj nie jest konieczne Wywołaj tę funkcję jawnie.

Aby uzyskać więcej informacji, zobacz [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDropSource](../../mfc/reference/coledropsource-class.md)
