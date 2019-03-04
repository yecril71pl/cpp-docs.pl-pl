---
title: CRichEditDoc Class
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
ms.openlocfilehash: 4c2021128dcc06a76cf3b68c0ec49b72a5860046
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295139"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc Class

Za pomocą [CRichEditView](../../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), zapewnia funkcję rozwiniętej kontroli edycji w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Wywołana w celu przeprowadzenia czyszczenia dokumentu.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Wskazuje, czy strumień danych wejściowych i wyjściowych powinna zawierać informacje o formatowaniu.|
|[CRichEditDoc::GetView](#getview)|Pobiera asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Wskazuje, czy strumień we/wy powinna zawierać formatowania.|

## <a name="remarks"></a>Uwagi

"Kontrolki edycji wzbogaconej" to okno, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać znaków i formatowanie akapitów i mogą zawierać osadzonych obiektów OLE. Kontrolki edycji wzbogaconej dostarczające interfejs programowania do formatowania tekstu. Jednak aplikacja musi zaimplementować wszelkie niezbędne udostępnić użytkownikowi operacji formatowania składników interfejsu użytkownika.

`CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę elementów klienta, które znajdują się w widoku. `CRichEditCntrItem` zapewnia dostęp po stronie kontenera elementów OLE w klienta.

Ten formant Windows wspólnej (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i pokrewne klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Przykład przy użyciu bogatej edycji dokumentu w aplikacji MFC, zobacz [WORDPAD](../../visual-cpp-samples.md) przykładowej aplikacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxrich.h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

Wywołaj tę funkcję, aby utworzyć `CRichEditCntrItem` obiektu i dodaj go do tego dokumentu.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parametry

*preo*<br/>
Wskaźnik do [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktury, które opisują elementu OLE. Nowy `CRichEditCntrItem` obiekt jest konstruowany wokół tego elementu OLE. Jeśli *preo* ma wartość NULL, nowy element klienta jest pusta.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu, która została dodana do tego dokumentu.

### <a name="remarks"></a>Uwagi

Ta funkcja nie wykonuje żadnych Inicjalizacja OLE.

Aby uzyskać więcej informacji, zobacz [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) struktury w zestawie Windows SDK.

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

Wywołaj tę funkcję, aby określić format tekstu dla przesyłania strumieniowego zawartości bogatej edycji.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeden z następujących flag:

- SF_TEXT wskazuje formant edycji wzbogaconej nie przechowuje informacje o formatowaniu.

- SF_RTF wskazuje formant edycji wzbogaconej zachować informacje o formatowaniu.

### <a name="remarks"></a>Uwagi

Wartość zwracana, opiera się na [m_bRTF](#m_brtf) element członkowski danych. Ta funkcja zwraca SF_RTF, jeśli `m_bRTF` jest wartość TRUE, a w przeciwnym razie SF_TEXT.

##  <a name="getview"></a>  CRichEditDoc::GetView

Wywołaj tę funkcję, aby uzyskać dostęp do [CRichEditView](../../mfc/reference/cricheditview-class.md) obiekt skojarzony z tym `CRichEditDoc` obiektu.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CRichEditView` obiekt skojarzony z dokumentem.

### <a name="remarks"></a>Uwagi

Tekst i informacje o formatowaniu są zawarte w `CRichEditView` obiektu. `CRichEditDoc` Obiekt przechowuje elementy OLE do serializacji. Powinien istnieć tylko jeden `CRichEditView` dla każdego `CRichEditDoc`.

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

W przypadku wartości TRUE oznacza, że [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) i [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) należy przechowywać w akapicie i cech formatowania znaków.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Zobacz także

[Próbki MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)<br/>
[Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Klasa CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)
