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
ms.openlocfilehash: 4683e0ea4a56e6766c039b2fcb858a54e28d14ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443348"
---
# <a name="cricheditcntritem-class"></a>Klasa CRichEditCntrItem

Za pomocą [CRichEditView](../../mfc/reference/cricheditview-class.md) i [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), zapewnia funkcję rozwiniętej kontroli edycji w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Konstruuje `CRichEditCntrItem` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Uaktywnia elementu jako innego typu.|

## <a name="remarks"></a>Uwagi

"Kontrolki edycji wzbogaconej" to okno, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać znaków i formatowanie akapitów i mogą zawierać osadzonych obiektów OLE. Kontrolki edycji wzbogaconej dostarczające interfejs programowania do formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie niezbędne udostępnić użytkownikowi operacji formatowania składników interfejsu użytkownika.

`CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę elementów klienta OLE, które znajdują się w widoku. `CRichEditCntrItem` udostępnia siebie kontener elementu klienta OLE.

Ten formant Windows wspólnej (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i pokrewne klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Przykład przy użyciu bogatej edycji kontenerów elementów w aplikacji MFC, zobacz [WORDPAD](../../visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

Wywołaj tę funkcję, aby utworzyć `CRichEditCntrItem` obiektu i dodaj go do dokumentu kontenera.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Wskaźnik do [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktury, które opisują elementu OLE. Nowy `CRichEditCntrItem` obiekt jest konstruowany wokół tego elementu OLE. Jeśli *preo* ma wartość NULL, element klienta jest pusty.

*pContainer*<br/>
Wskaźnik do dokumentu kontenera, który będzie zawierać tego elementu. Jeśli *element pContainer* ma wartość NULL, należy jawnie wywołać [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) można dodać tego elementu klienta do dokumentu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie wykonuje żadnych Inicjalizacja OLE.

Aby uzyskać więcej informacji, zobacz [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktury w zestawie Windows SDK.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Wywołaj tę funkcję, aby zsynchronizować aspektu urządzenia [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), to `CRichEditCntrltem` do określonej przez *Otwórz*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parametry

*Otwórz*<br/>
Odwołanie do [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktury, które opisują elementu OLE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbki MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
