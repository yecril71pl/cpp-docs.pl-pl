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
ms.openlocfilehash: d93eb3de87b50f337f0d3edad65f5dc3013e8327
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127460"
---
# <a name="coledropsource-class"></a>Klasa COleDropSource

Umożliwia przeciąganie danych do miejsca docelowego upuszczania.

## <a name="syntax"></a>Składnia

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|Konstruuje obiekt `COleDropSource`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleDropSource:: GiveFeedback](#givefeedback)|Zmienia kursor w trakcie operacji przeciągania i upuszczania.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Obsługuje przechwytywanie myszy podczas operacji przeciągania i upuszczania.|
|[COleDropSource:: QueryContinueDrag](#querycontinuedrag)|Sprawdza, czy przeciąganie ma być kontynuowane.|

## <a name="remarks"></a>Uwagi

Klasa [COleDropTarget](../../mfc/reference/coledroptarget-class.md) obsługuje część otrzymującą operacji przeciągania i upuszczania. Obiekt `COleDropSource` jest odpowiedzialny za określenie, kiedy rozpoczyna się operacja przeciągania, dostarczając opinię podczas operacji przeciągania i określając, kiedy się skończy.

Aby użyć obiektu `COleDropSource`, należy wywołać konstruktora. Upraszcza to proces określania zdarzeń, takich jak kliknięcie myszą, rozpoczęcie operacji przeciągania przy użyciu [by uzyskać COleDataSource::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)lub [COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) funkcji. Te funkcje spowodują utworzenie obiektu `COleDropSource`. Możesz chcieć zmodyfikować domyślne zachowanie funkcji `COleDropSource`. Te funkcje członkowskie będą wywoływane w odpowiednim czasie przez platformę.

Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania przy użyciu technologii OLE, zobacz artykuł [OLE przeciągnij i upuść](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

Konstruuje obiekt `COleDropSource`.

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: GiveFeedback

Wywoływane przez platformę po wywołaniu [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) lub [COleDropTarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Parametry

*dropEffect*<br/>
Efekt, który ma być wyświetlany użytkownikowi, zwykle wskazujący, co się stanie, Jeśli pozostało w tym punkcie z wybranymi danymi. Zwykle jest to wartość zwrócona przez ostatnie wywołanie [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) lub [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover). Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_NONE upuszczenie nie jest dozwolone.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- Zostanie ustanowione DROPEFFECT_LINK łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL operacja przewijania przeciągnij ma miejsce lub występuje w elemencie docelowym.

### <a name="return-value"></a>Wartość zwrócona

Zwraca DRAGDROP_S_USEDEFAULTCURSORS, jeśli przeciąganie jest w toku, NOERROR, jeśli nie jest.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby przekazać użytkownikowi opinię na temat tego, co się stanie, jeśli w tym punkcie Wystąpił błąd. Domyślna implementacja używa domyślnych kursorów OLE. Aby uzyskać więcej informacji na temat operacji przeciągania i upuszczania przy użyciu technologii OLE, zobacz artykuł [OLE przeciągnij i upuść](../../mfc/drag-and-drop-ole.md).

Aby uzyskać więcej informacji, zobacz [IDropSource:: GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)i [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) w Windows SDK.

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Wywoływane przez platformę, gdy wystąpi zdarzenie, które może rozpocząć operację przeciągania, taką jak naciśnięcie lewego przycisku myszy.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okno, które zawiera wybrane dane.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli przeciąganie jest dozwolone, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, jeśli chcesz zmodyfikować sposób uruchomienia procesu przeciągania. Domyślna implementacja przechwytuje mysz i pozostaje w trybie przeciągania, dopóki użytkownik kliknie lewy lub prawy przycisk myszy lub trafi klawisz ESC, po którym zwolni mysz.

##  <a name="querycontinuedrag"></a>COleDropSource:: QueryContinueDrag

Po rozpoczęciu przeciągania ta funkcja jest wywoływana wielokrotnie przez platformę, dopóki operacja przeciągania nie zostanie anulowana ani zakończona.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Parametry

*bEscapePressed*<br/>
Określa, czy klawisz ESC został naciśnięty od czasu ostatniego wywołania do `COleDropSource::QueryContinueDrag`.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących na klawiaturze. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

### <a name="return-value"></a>Wartość zwrócona

DRAGDROP_S_CANCEL, jeśli klawisz ESC lub prawy przycisk jest wciśnięty, lub przycisk lewy jest uruchamiany przed rozpoczęciem przeciągania. DRAGDROP_S_DROP, jeśli operacja upuszczania powinna wystąpić. W przeciwnym razie S_OK.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, jeśli chcesz zmienić punkt, w którym przeciąganie zostało anulowane, lub upuść.

Implementacja domyślna inicjuje upuszczenie lub anuluje przeciąganie w następujący sposób. Anuluje operację przeciągania po naciśnięciu klawisza ESC lub prawego przycisku myszy. Inicjuje operację upuszczania, gdy po rozpoczęciu przeciągania zostanie podniesiony lewy przycisk myszy. W przeciwnym razie zwraca S_OK i nie wykonuje żadnych dalszych operacji.

Ponieważ ta funkcja jest wywoływana często, należy ją zoptymalizować jak najwięcej.

## <a name="see-also"></a>Zobacz też

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
