---
title: Klasa CDocItem
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375623"
---
# <a name="cdocitem-class"></a>Klasa CDocItem

Klasa podstawowa dla elementów dokumentu, które są składnikami danych dokumentu.

## <a name="syntax"></a>Składnia

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|Zwraca dokument zawierający element.|
|[CDocItem::IsBlank](#isblank)|Określa, czy element zawiera jakiekolwiek informacje.|

## <a name="remarks"></a>Uwagi

`CDocItem`obiekty są używane do reprezentowania elementów OLE w dokumentach klienta i serwera.

Aby uzyskać więcej informacji, zobacz artykuł [Kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument

Wywołanie tej funkcji, aby uzyskać dokument, który zawiera element.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, który zawiera element; NULL, jeśli element nie jest częścią dokumentu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zastępowana w klasach pochodnych [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md), zwracając wskaźnik do [COleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)lub [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) obiektu.

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank

Wywoływana przez platformę, gdy występuje domyślna serializacja.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli element nie zawiera żadnych informacji; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie `CDocItem` obiekty nie są puste. [COleClientItem](../../mfc/reference/coleclientitem-class.md) obiekty są czasami puste, ponieważ `CDocItem`pochodzą bezpośrednio z . Jednak [COleServerItem](../../mfc/reference/coleserveritem-class.md) obiekty są zawsze puste. Domyślnie aplikacje OLE `COleClientItem` zawierające obiekty, które nie mają zakresu x lub y są serializowane. Odbywa się to przez zwrócenie true z `IsBlank` zastąpienia, gdy element nie ma zakresu x lub y.

Zastąd w tej funkcji, jeśli chcesz zaimplementować inne akcje podczas serializacji.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)
