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
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375524"
---
# <a name="cdocobjectserveritem-class"></a>Klasa CDocObjectServerItem

Implementuje zlecenia serwera OLE specjalnie dla serwerów DocObject.

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
|[CDocObjectServerItem::GetDocument](#getdocument)|Pobiera wskaźnik do dokumentu, który zawiera element.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Wywoływany do wykonania zlecenia.|
|[CDocObjectServerItem::OnHide](#onhide)|Zgłasza wyjątek, jeśli struktura próbuje ukryć element DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Wywoływane przez strukturę, aby element DocObject w miejscu aktywne. Jeśli element nie jest DocObject, wywołuje [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Uwagi

`CDocObjectServerItem`definiuje zastępowalne funkcje członkowskie: [OnHide](#onhide), [OnDoVerb](#ondoverb)i [OnShow](#onshow).

Aby `CDocObjectServerItem`użyć , upewnij się, że [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) zastąpić w `COleServerDoc` `CDocObjectServerItem` klasie pochodnej zwraca nowy obiekt. Jeśli chcesz zmienić dowolną funkcjonalność w elemencie, możesz `CDocObjectServerItem`utworzyć nowe wystąpienie własnej klasy pochodnej.

Aby uzyskać więcej informacji na temat DocObjects, zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołaniu MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocitem](../../mfc/reference/cdocitem-class.md)

[Coleserveritem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Konstruuje `CDocObjectServerItem` obiekt.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc (100)*<br/>
Wskaźnik do dokumentu, który będzie zawierał nowy element DocObject.

*bAutoDelete*<br/>
Wskazuje, czy obiekt można usunąć po zwolnieniu łącza do niego. Ustaw argument na FAŁSZ, `CDocObjectServerItem` jeśli obiekt jest integralną częścią danych dokumentu. Ustaw go na WARTOŚĆ PRAWDA, jeśli obiekt jest strukturą pomocniczą używaną do identyfikowania zakresu w danych dokumentu, który może zostać usunięty przez platformę.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument

Pobiera wskaźnik do dokumentu, który zawiera element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, który zawiera element; NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu dostęp do dokumentu serwera, który został przekazany jako argument do konstruktora [CDocObjectServerItem.](#cdocobjectserveritem)

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServerItem::OnDoVerb

Wywoływane przez strukturę do wykonania określonego zlecenia.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Określa zlecenie do wykonania. Aby uzyskać możliwe wartości, zobacz [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) w windows SDK.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje [OnShow](#onshow) funkcji elementu członkowskiego, jeśli element jest DocObject i OLEIVERB_INPLACEACTIVATE lub OLEIVERB_SHOW jest określony. Jeśli element nie jest DocObject lub inny zlecenie jest określony, domyślna implementacja wywołuje [COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide

Wywoływana przez strukturę, aby ukryć element.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja zgłasza wyjątek, jeśli element jest DocObject. Nie można ukryć aktywnego elementu DocObject, ponieważ ma on cały widok. Należy dezaktywować element DocObject, aby zniknął. Jeśli element nie jest DocObject, domyślna implementacja wywołuje [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow

Wywoływane przez strukturę, aby poinstruować aplikację serwera, aby element DocObject w miejscu aktywne.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Jeśli element nie jest DocObject, domyślna implementacja wywołuje [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Zastąpuj tę funkcję, jeśli chcesz wykonać specjalne przetwarzanie podczas otwierania elementu DocObject.

## <a name="see-also"></a>Zobacz też

[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)<br/>
[Klasa COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
