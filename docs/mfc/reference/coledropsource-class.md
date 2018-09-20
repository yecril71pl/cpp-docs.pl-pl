---
title: Klasa COleDropSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f40ac527ba8ad7e65f025910e96a69f546842e30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447560"
---
# <a name="coledropsource-class"></a>Klasa COleDropSource

Umożliwia danych można przeciągnąć do miejsca docelowego.

## <a name="syntax"></a>Składnia

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Konstruuje `COleDropSource` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDropSource::GiveFeedback](#givefeedback)|Kursor zmienia się podczas operacji przeciągania i upuszczania.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Obsługuje przechwytywanie myszy podczas operacji przeciągania i upuszczania.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Sprawdza, czy przeciąganie powinno być kontynuowane.|

## <a name="remarks"></a>Uwagi

[COleDropTarget](../../mfc/reference/coledroptarget-class.md) klasa obsługuje odbieranie część operacji przeciągania i upuszczania. `COleDropSource` Obiekt jest odpowiedzialny za określenie, kiedy rozpoczyna się operacja przeciągania, opinii, podczas operacji przeciągania i określania, kiedy kończy się operacja przeciągania.

Aby użyć `COleDropSource` obiektów, po prostu wywołanie konstruktora. Upraszcza to proces określania, jakie zdarzenia, takie jak kliknięcie myszą, rozpocząć operację przeciągania przy użyciu [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), lub [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkcji. Tych funkcji spowoduje utworzenie `COleDropSource` obiekt dla Ciebie. Możesz chcieć zmodyfikować domyślne zachowanie `COleDropSource` funkcje z możliwością zastąpienia. Te funkcje elementów członkowskich zostanie wywołana przez strukturę w odpowiednim czasie.

Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą mechanizmu OLE, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="coledropsource"></a>  COleDropSource::COleDropSource

Konstruuje `COleDropSource` obiektu.

```
COleDropSource();
```

##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback

Wywoływane przez platformę po wywołaniu [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) lub [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*dropEffect*<br/>
Efekt, który chcesz wyświetlić użytkownikowi, zazwyczaj wskazujący, co się stanie, jeśli zrzutu wystąpił na tym etapie przy użyciu wybranych danych. Zazwyczaj jest to wartość zwracana przez wywołanie najnowszych [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) lub [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Może być co najmniej jeden z następujących czynności:

- DROPEFFECT_NONE zrzutu będzie niedozwolone.

- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.

- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.

- Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.

- Operacja przewijania przeciągania A DROPEFFECT_SCROLL może nastąpić lub odbywa się w elemencie docelowym.

### <a name="return-value"></a>Wartość zwracana

Zwraca DRAGDROP_S_USEDEFAULTCURSORS Jeśli przeciąganie jest w toku, brak błędu, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby przekazać opinię do użytkownika o co się stanie, jeśli w tym momencie zrzutu. Domyślna implementacja używa kursory domyślne OLE. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania za pomocą mechanizmu OLE, zobacz artykuł [przeciąganie i upuszczanie (OLE)](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource::GiveFeedback](/windows/desktop/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover), i [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) w zestawie Windows SDK.

##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które można rozpocząć operacji przeciągania, takich jak naciśnięcie klawisza lewego przycisku myszy.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okna zawierającego wybrane dane.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli przeciąganie może, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, jeśli chcesz zmodyfikować sposób, w jaki przeciągania proces jest uruchomiony. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągnij, dopóki użytkownik kliknie przycisk myszy w lewo lub w prawo lub liczba trafień ESC, co zwalnia wskaźnik myszy.

##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag

Po rozpoczęciu przeciąganie ta funkcja jest wywoływana wielokrotnie przez platformę, do momentu anulowania lub ukończyć operacji przeciągania.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
Stany, czy od ostatniego wywołania, aby został naciśnięty klawisz ESC `COleDropSource::QueryContinueDrag`.

*dwKeyState*<br/>
Zawiera stan klawisze modyfikujące na klawiaturze. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

### <a name="return-value"></a>Wartość zwracana

DRAGDROP_S_CANCEL Jeśli klawisz ESC lub prawy przycisk jest wciśnięty lub left przycisk jest wywoływane przed uruchomieniem. DRAGDROP_S_DROP, jeżeli wystąpi operacja przeciągania. W przeciwnym razie S_OK.

### <a name="remarks"></a>Uwagi

Występuje, zastąpienie, który tę funkcję, jeśli chcesz zmienić punkt, w których przeciąganie zostało anulowane lub zrzutu.

Domyślna implementacja inicjuje listy lub Anuluje przeciąganie w następujący sposób. Gdy zostanie naciśnięty klawisz ESC lub prawego przycisku myszy, anuluje operację przeciągania. Jeśli lewy przycisk myszy jest wywoływane po rozpoczął przeciąganie, inicjuje operacja przeciągania. W przeciwnym razie zwraca wartość S_OK i wykonuje nie dalszych operacji.

Ponieważ ta funkcja jest często wywoływana, należy można zoptymalizować możliwie.

## <a name="see-also"></a>Zobacz też

[Próbki MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Próbki MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)



