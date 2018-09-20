---
title: Klasa CDocObjectServerItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5dad01bb73f04482b15e345451a0a4a6a069985
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396406"
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
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Konstruuje `CDocObjectServerItem` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Pobiera wskaźnik do dokumentu, który zawiera element.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Zgłasza wyjątek, jeśli struktura próbuje ukryć element DocObject.|
|[CDocObjectServerItem::OnHide](#onhide)|Zgłasza wyjątek, jeśli struktura próbuje ukryć element DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Wywoływane przez platformę, aby element DocObject elementu w miejscu active. Jeśli element nie jest obiekt DocObject, wywołuje metodę [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Uwagi

`CDocObjectServerItem` Definiuje funkcje Członkowskie z możliwością: [OnHide](#onhide), [OnDoVerb](#ondoverb), i [metodzie OnShow](#onshow).

Aby użyć `CDocObjectServerItem`, zapewnić, że [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) zastąpić w usługi `COleServerDoc`— klasie pochodnej zwraca nowy `CDocObjectServerItem` obiektu. Jeśli musisz zmienić żadnych funkcji Twojego elementu, można utworzyć nowe wystąpienie klasy własne `CDocObjectServerItem`-klasy pochodnej.

Aby uzyskać więcej informacji na temat DocObjects zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołanie MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

Konstruuje `CDocObjectServerItem` obiektu.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*pServerDoc*<br/>
Wskaźnik do dokumentu, który będzie zawierać nowy element DocObject.

*bAutoDelete*<br/>
Wskazuje, czy obiekt może zostać usunięty po udostępnieniu do niej łącza. Argument ma wartość FAŁSZ Jeśli `CDocObjectServerItem` obiekt jest integralną częścią danych dokumentu. Ustaw ją na wartość TRUE, jeśli obiekt jest struktura dodatkowych, używany do identyfikowania zakres danych dokumentu, który może zostać usunięta przez platformę.

##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument

Pobiera wskaźnik do dokumentu, który zawiera element.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, który zawiera element; Wartość NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu dostęp do dokumentu serwera, który jest przekazywany jako argument do [CDocObjectServerItem](#cdocobjectserveritem) konstruktora.

##  <a name="onhide"></a>  CDocObjectServerItem::OnHide

Metoda wywoływana przez platformę, by ukryć element.

```
virtual void OnHide();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja zgłasza wyjątek, jeśli element znajduje się obiekt DocObject. Nie można ukryć aktywny element DocObject, ponieważ trwa całego widoku. Należy zdezaktywować element DocObject, aby zniknął. Jeśli element nie jest obiekt DocObject, domyślna implementacja wywołuje [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>  CDocObjectServerItem::OnShow

Metoda wywoływana przez platformę w celu poinstruowania aplikacji serwera, aby element DocObject elementu w miejscu active.

```
virtual void OnShow();
```

### <a name="remarks"></a>Uwagi

Jeśli element nie jest obiekt DocObject, domyślna implementacja wywołuje [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania podczas otwierania elementu DocObject.

## <a name="see-also"></a>Zobacz też

[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)<br/>
[Klasa COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
