---
title: Klasa CRichEditDoc
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368262"
---
# <a name="cricheditdoc-class"></a>Klasa CRichEditDoc

Z [CRichEditView](../../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), zapewnia funkcjonalność formantu edycji bogatej w kontekście architektury widoku dokumentów MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Wywoływana do czyszczenia dokumentu.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Wskazuje, czy dane wejściowe i wyjściowe strumienia powinny zawierać informacje o formatowaniu.|
|[CRichEditDoc::GetView](#getview)|Pobiera asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Wskazuje, czy we/wy strumienia powinny zawierać formatowanie.|

## <a name="remarks"></a>Uwagi

"Formant edycji bogatej" to okno, w którym użytkownik może wprowadzać i edytować tekst. Tekst może być przypisany do formatowania znaków i akapitów i może zawierać osadzone obiekty OLE. Zaawansowane kontrolki edycji zapewniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika niezbędne do udostępnienia użytkownikowi operacji formatowania.

`CRichEditView`zachowuje charakterystykę tekstu i formatowania tekstu. `CRichEditDoc`utrzymuje listę elementów klienta, które są w widoku. `CRichEditCntrItem`zapewnia dostęp po stronie kontenera do elementów klienta OLE.

Ta wspólna kontrola systemu Windows (a zatem [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i powiązane klasy) jest dostępna tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersjach 3.51 i nowszych.

Na przykład przy użyciu dokumentu edycji bogatej w aplikacji MFC, zobacz [wordpad](../../overview/visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocument](../../mfc/reference/cdocument-class.md)

[Coledocument](../../mfc/reference/coledocument-class.md)

[Colelinkingdoc](../../mfc/reference/colelinkingdoc-class.md)

[Coleserverdoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>CRichEditDoc::CreateClientItem

Wywołanie tej funkcji, aby utworzyć `CRichEditCntrItem` obiekt i dodać go do tego dokumentu.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Wskaźnik do struktury [REOBJECT,](/windows/win32/api/richole/ns-richole-reobject) który opisuje element OLE. Nowy `CRichEditCntrItem` obiekt jest zbudowany wokół tego elementu OLE. Jeśli *preo* ma wartość NULL, nowy element klienta jest pusty.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego [obiektu CRichEditCntrItem,](../../mfc/reference/cricheditcntritem-class.md) który został dodany do tego dokumentu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie wykonuje inicjowania OLE.

Aby uzyskać więcej informacji, zobacz strukturę [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) w windows SDK.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat

Wywołanie tej funkcji, aby określić format tekstu do przesyłania strumieniowego zawartości edycji bogatej.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedna z następujących flag:

- SF_TEXT Wskazuje, że formant edycji rich nie przechowuje informacji o formatowaniu.

- SF_RTF Wskazuje, że formant edycji rozszerzonej zachowuje informacje o formatowaniu.

### <a name="remarks"></a>Uwagi

Zwracana wartość jest oparta na [m_bRTF](#m_brtf) element członkowski danych. Ta funkcja zwraca SF_RTF, `m_bRTF` jeśli ma wartość PRAWDA; w przeciwnym razie SF_TEXT.

## <a name="cricheditdocgetview"></a><a name="getview"></a>CRichEditDoc::GetView

Wywołanie tej funkcji, aby uzyskać dostęp do `CRichEditDoc` [CRichEditView](../../mfc/reference/cricheditview-class.md) obiektu skojarzonego z tym obiektem.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRichEditView` obiektu skojarzonego z dokumentem.

### <a name="remarks"></a>Uwagi

Informacje tekstowe i formatujące znajdują `CRichEditView` się w obiekcie. Obiekt `CRichEditDoc` przechowuje elementy OLE do serializacji. Powinien być tylko `CRichEditView` jeden `CRichEditDoc`dla każdego .

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>CRichEditDoc::m_bRTF

Gdy TRUE, wskazuje, że [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) i [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) należy przechowywać akapitu i znaków właściwości formatowania.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Zobacz też

[Przykładowy program WORDPAD mfc](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)<br/>
[Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)
