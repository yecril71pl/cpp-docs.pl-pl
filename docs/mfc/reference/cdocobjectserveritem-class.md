---
title: Klasa CDocObjectServerItem
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 4d44791415626f1a94500b9c3885581d67e8fe42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506819"
---
# <a name="cdocobjectserveritem-class"></a>Klasa CDocObjectServerItem

Implementuje zlecenia serwera OLE przeznaczone dla serwerów DocObject.

## <a name="syntax"></a>Składnia

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Konstruuje `CDocObjectServerItem` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem:: GetDocument](#getdocument)|Pobiera wskaźnik do dokumentu zawierającego element.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Wywołuje się, by wykonać czasownik.|
|[CDocObjectServerItem:: OnHide](#onhide)|Zgłasza wyjątek, jeśli struktura podejmie próbę ukrycia elementu DocObject.|
|[CDocObjectServerItem:: OnShow](#onshow)|Wywoływane przez platformę, aby element DocObject był aktywny. Jeśli element nie jest DocObject, wywołuje [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Uwagi

`CDocObjectServerItem`definiuje funkcje składowe, które są możliwe do zastąpienia: [OnHide](#onhide), [OnDoVerb](#ondoverb)i OnShow. [](#onshow)

Aby użyć `CDocObjectServerItem`, należy się upewnić, że przesłonięcie [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) w `COleServerDoc`klasie pochodnej `CDocObjectServerItem` zwraca nowy obiekt. Jeśli trzeba zmienić dowolne funkcje w elemencie, można utworzyć nowe wystąpienie `CDocObjectServerItem`klasy pochodnej.

Aby uzyskać więcej informacji na temat DocObjects, zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *dokumentacji MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob. h

##  <a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Konstruuje `CDocObjectServerItem` obiekt.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Wskaźnik do dokumentu, który będzie zawierać nowy element DocObject.

*bAutoDelete*<br/>
Wskazuje, czy obiekt może zostać usunięty po wydaniu linku do niego. Dla argumentu ustaw wartość false, jeśli `CDocObjectServerItem` obiekt jest integralną częścią danych dokumentu. Ustaw wartość na TRUE, jeśli obiekt jest strukturą pomocniczą służącą do identyfikowania zakresu w danych dokumentu, który może zostać usunięty przez platformę.

##  <a name="getdocument"></a>CDocObjectServerItem:: GetDocument

Pobiera wskaźnik do dokumentu zawierającego element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu zawierającego element; Wartość NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Pozwala to na dostęp do dokumentu serwera, który został przesłany jako argument do konstruktora [CDocObjectServerItem](#cdocobjectserveritem) .

##  <a name="ondoverb"></a>CDocObjectServerItem::OnDoVerb

Wywoływane przez platformę, by wykonać określone zlecenie.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Określa zlecenie do wykonania. Aby uzyskać możliwe wartości, zobacz [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w Windows SDK.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje funkcję elementu [](#onshow) Członkowskiego OnShow, jeśli element jest elementem DocObject i określono wartość OLEIVERB_INPLACEACTIVATE lub OLEIVERB_SHOW. Jeśli element nie jest DocObject lub określono inne zlecenie, domyślne wywołania implementacji [COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

##  <a name="onhide"></a>CDocObjectServerItem:: OnHide

Wywoływane przez platformę w celu ukrycia elementu.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Implementacja domyślna zgłasza wyjątek, jeśli element jest obiektem DocObject. Nie można ukryć aktywnego elementu DocObject, ponieważ pobiera on cały widok. Aby to zrobić, musisz dezaktywować element DocObject. Jeśli element nie jest DocObject, domyślne wywołania implementacji [COleServerItem:: OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>CDocObjectServerItem:: OnShow

Wywoływane przez platformę, by nakazać aplikacji serwerowej DocObject element w miejscu.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Jeśli element nie jest DocObject, domyślne wywołania implementacji [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Przesłoń tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas otwierania elementu DocObject.

## <a name="see-also"></a>Zobacz także

[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)<br/>
[Klasa COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
