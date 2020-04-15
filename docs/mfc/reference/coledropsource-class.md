---
title: Klasa COleDropSource
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375022"
---
# <a name="coledropsource-class"></a>Klasa COleDropSource

Umożliwia przeciąganie danych do celu upuszczania.

## <a name="syntax"></a>Składnia

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Konstruuje `COleDropSource` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Zmienia kursor podczas operacji przeciągania i upuszczania.|
|[COleDropSource::OnBegindrag](#onbegindrag)|Obsługuje przechwytywanie myszy podczas operacji przeciągania i upuszczania.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Sprawdza, czy przeciąganie powinno być kontynuowane.|

## <a name="remarks"></a>Uwagi

[COleDropTarget](../../mfc/reference/coledroptarget-class.md) Klasa obsługuje odbieranie część operacji przeciągania i upuszczania. Obiekt `COleDropSource` jest odpowiedzialny za określenie, kiedy rozpoczyna się operacja przeciągania, przekazywanie informacji zwrotnych podczas operacji przeciągania i określanie, kiedy kończy się operacja przeciągania.

Aby użyć `COleDropSource` obiektu, wystarczy wywołać konstruktora. Upraszcza to proces określania, jakie zdarzenia, takie jak kliknięcie myszą, rozpocząć operację przeciągania przy użyciu [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)lub [COleServerItem::DoDragDrop,](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkcja. Te funkcje `COleDropSource` utworzy obiekt dla Ciebie. Można zmodyfikować domyślne zachowanie `COleDropSource` funkcji, które można zastąpić. Te funkcje członkowskie będą wywoływane w odpowiednim czasie przez ramy.

Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania przy użyciu ole, zobacz artykuł [OLE przeciągania i upuszczania](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) w windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDropSource::COleDropSource

Konstruuje `COleDropSource` obiekt.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDropSource::GiveFeedback

Wywoływane przez platformę po wywołaniu [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) lub [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*dropEffect (efekt upuszczania)*<br/>
Efekt, który chcesz wyświetlić użytkownikowi, zwykle wskazując, co by się stało, gdyby w tym momencie wystąpił spadek z wybranymi danymi. Zazwyczaj jest to wartość zwracana przez ostatnie wywołanie [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) lub [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Może to być co najmniej jeden z następujących:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca DRAGDROP_S_USEDEFAULTCURSORS jeśli przeciąganie jest w toku, NOERROR, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Zastądnij tę funkcję, aby przekazać użytkownikowi opinię o tym, co by się stało, gdyby w tym momencie wystąpił spadek. Domyślna implementacja używa kursorów domyślnych OLE. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania przy użyciu ole, zobacz artykuł [OLE przeciągania i upuszczania](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource::GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)i [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) w windows SDK.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDropSource::OnBegindrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które może rozpocząć operację przeciągania, takie jak naciśnięcie lewego przycisku myszy.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno zawierające wybrane dane.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy zmodyfikować sposób rozpoczynania procesu przeciągania. Domyślna implementacja przechwytuje myszy i pozostaje w trybie przeciągania, dopóki użytkownik nie kliknie lewego lub prawego przycisku myszy lub nie uderzy ESC, w którym to czasie zwalnia mysz.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag

Po rozpoczęciu przeciągania ta funkcja jest wywoływana wielokrotnie przez platformę, dopóki operacja przeciągania nie zostanie anulowana lub zakończona.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
określa, czy klucz ESC został wciśnięty `COleDropSource::QueryContinueDrag`od ostatniego wezwania do .

*dwKeyState (Stan klucza)*<br/>
Zawiera stan klawiszy modyfikatora na klawiaturze. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

### <a name="return-value"></a>Wartość zwracana

DRAGDROP_S_CANCEL, jeśli zostanie naciśnięty klawisz ESC lub prawy przycisk lub lewy przycisk jest podnoszony przed rozpoczęciem przeciągania. DRAGDROP_S_DROP, jeśli powinna wystąpić operacja upuszczania. W przeciwnym razie S_OK.

### <a name="remarks"></a>Uwagi

Zastądnij tę funkcję, jeśli chcesz zmienić punkt, w którym przeciąganie jest anulowane lub występuje upuszczenie.

Domyślna implementacja inicjuje upuszczenie lub anuluje przeciąganie w następujący sposób. Anuluje operację przeciągania po naciśnięciu klawisza ESC lub prawego przycisku myszy. Inicjuje operację upuszczania, gdy lewy przycisk myszy jest wywoływany po rozpoczęciu przeciągania. W przeciwnym razie zwraca S_OK i nie wykonuje żadnych dalszych operacji.

Ponieważ ta funkcja jest często wywoływana, należy zoptymalizować jak najwięcej.

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
