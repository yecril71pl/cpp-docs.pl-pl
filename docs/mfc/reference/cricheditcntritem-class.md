---
title: Klasa CRichEditCntrItem
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 7b566fe7f1c0667dbcdb4976f79cd2e1597f48f6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752772"
---
# <a name="cricheditcntritem-class"></a>Klasa CRichEditCntrItem

Z [CRichEditView](../../mfc/reference/cricheditview-class.md) i [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zapewnia funkcjonalność formantu edycji bogatej w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Konstruuje `CRichEditCntrItem` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktywuje element jako inny typ.|

## <a name="remarks"></a>Uwagi

"Formant edycji bogatej" to okno, w którym użytkownik może wprowadzać i edytować tekst. Tekst może być przypisany do formatowania znaków i akapitów i może zawierać osadzone obiekty OLE. Zaawansowane kontrolki edycji zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania.

`CRichEditView`zachowuje charakterystykę tekstu i formatowania tekstu. `CRichEditDoc`utrzymuje listę elementów klienta OLE, które są w widoku. `CRichEditCntrItem`zapewnia dostęp po stronie kontenera do elementu klienta OLE.

Ta wspólna kontrola systemu Windows (a zatem [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i powiązane klasy) jest dostępna tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersjach 3.51 i nowszych.

Na przykład przy użyciu elementów kontenera edycji rozszerzonej w aplikacji MFC, zobacz [wordpad](../../overview/visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocitem](../../mfc/reference/cdocitem-class.md)

[Coleclientitem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem

Wywołanie tej funkcji, aby utworzyć `CRichEditCntrItem` obiekt i dodać go do dokumentu kontenera.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Wskaźnik do struktury [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) który opisuje element OLE. Nowy `CRichEditCntrItem` obiekt jest zbudowany wokół tego elementu OLE. Jeśli *preo* ma wartość NULL, element klienta jest pusty.

*pKontener*<br/>
Wskaźnik do dokumentu kontenera, który będzie zawierał ten element. Jeśli *pContainer* ma wartość NULL, należy jawnie wywołać [COleDocument::AddItem,](../../mfc/reference/coledocument-class.md#additem) aby dodać ten element klienta do dokumentu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie wykonuje inicjowania OLE.

Aby uzyskać więcej informacji, zobacz strukturę [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) w windows SDK.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject

Wywołanie tej funkcji, aby zsynchronizować aspekt `CRichEditCntrltem` urządzenia, [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), z tym określonym przez *reo*.

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parametry

*Reo*<br/>
Odwołanie do struktury [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) która opisuje element OLE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) w windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykładowy program WORDPAD mfc](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
