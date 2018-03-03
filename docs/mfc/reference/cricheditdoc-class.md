---
title: "Cricheditdoc — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
dev_langs:
- C++
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c427dc034a37bf3b0686b0fd95e62c3b718fbaea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cricheditdoc-class"></a>Cricheditdoc — klasa
Z [cricheditview —](../../mfc/reference/cricheditview-class.md) i [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), udostępnia funkcje kontrolki zaawansowanej edycji w kontekście architektura widoku dokumentu MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CRichEditDoc : public COleServerDoc  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](#createclientitem)|Wywołuje się, by wykonać czyszczenie dokumentu.|  
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Wskazuje, czy strumień danych wejściowych i wyjściowych powinna zawierać informacje dotyczące formatowania.|  
|[CRichEditDoc::GetView](#getview)|Pobiera asssociated [cricheditview —](../../mfc/reference/cricheditview-class.md) obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRichEditDoc::m_bRTF](#m_brtf)|Wskazuje, czy we/wy strumienia ma uwzględniać formatowania.|  
  
## <a name="remarks"></a>Uwagi  
 "Kontrolki zaawansowanej edycji" jest oknem, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać formatowanie znaków i akapitów i mogą zawierać osadzonych obiektów OLE. Formanty edycji wzbogaconej udostępniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika należy udostępnić użytkownikowi operacji formatowania.  
  
 `CRichEditView`przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc`przechowuje listę elementów klienta, które znajdują się w widoku. `CRichEditCntrItem`udostępnia kontener serwerowe elementy klienckie OLE.  
  
 Ten formant wspólne systemu Windows (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i związanych z klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Na przykład za pomocą zaawansowanej edycji dokumentu w aplikacji MFC, zobacz [WORDPAD](../../visual-cpp-samples.md) przykładowej aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrich.h  
  
##  <a name="createclientitem"></a>CRichEditDoc::CreateClientItem  
 Wywołanie tej funkcji, aby utworzyć `CRichEditCntrItem` obiektu i dodaj go do tego dokumentu.  
  
```  
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *preo*  
 Wskaźnik do [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) strukturę, która opisuje element OLE. Nowe `CRichEditCntrItem` konstruowania obiektu wokół tego elementu OLE. Jeśli *preo* jest **NULL**, nowy element klienta jest pusta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) obiektu, który został dodany do tego dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie wykonuje żadnych inicjowania OLE.  
  
 Aby uzyskać więcej informacji, zobacz [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktury w zestawie Windows SDK.  
  
##  <a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat  
 Wywołanie tej funkcji, aby określić format tekstu dla przesyłanie strumieniowe zawartości zaawansowanej edycji.  
  
```  
int GetStreamFormat() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden z następujących flag:  
  
- `SF_TEXT`Wskazuje, że kontrolki zaawansowanej edycji nie przechowuje informacje dotyczące formatowania.  
  
- `SF_RTF`Wskazuje, że kontrolki zaawansowanej edycji przechowują formatowania.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana opiera się na [m_bRTF](#m_brtf) element członkowski danych. Ta funkcja zwraca `SF_RTF` Jeśli `m_bRTF` jest **TRUE**; w przeciwnym razie `SF_TEXT`.  
  
##  <a name="getview"></a>CRichEditDoc::GetView  
 Wywołanie tej funkcji, aby uzyskać dostęp do [cricheditview —](../../mfc/reference/cricheditview-class.md) obiekt skojarzony z tym `CRichEditDoc` obiektu.  
  
```  
virtual CRichEditView* GetView() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CRichEditView` obiekt skojarzony z dokumentem.  
  
### <a name="remarks"></a>Uwagi  
 Tekst i informacje dotyczące formatowania są zawarte w `CRichEditView` obiektu. `CRichEditDoc` Obiekt przechowuje elementy OLE do serializacji. Powinny istnieć tylko jedna `CRichEditView` dla każdego `CRichEditDoc`.  
  
##  <a name="m_brtf"></a>CRichEditDoc::m_bRTF  
 Gdy **TRUE**, oznacza to, że [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) i [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) należy przechowywać akapitu i formatowanie znaków właściwości.  
  
```  
BOOL m_bRTF;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC WORDPAD](../../visual-cpp-samples.md)   
 [Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cricheditview — klasa](../../mfc/reference/cricheditview-class.md)   
 [Klasa CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)   
 [Klasa COleDocument](../../mfc/reference/coledocument-class.md)   
 [Klasa CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)
