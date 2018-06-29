---
title: Klasa CRichEditCntrItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b4c038389810fcc6a847cdbf7837568b3007b6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078611"
---
# <a name="cricheditcntritem-class"></a>Klasa CRichEditCntrItem
Z [cricheditview —](../../mfc/reference/cricheditview-class.md) i [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md), udostępnia funkcje kontrolki zaawansowanej edycji w kontekście architektura widoku dokumentu MFC.  
  
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
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktywuje element jako innego typu.|  
  
## <a name="remarks"></a>Uwagi  
 "Kontrolki zaawansowanej edycji" jest oknem, w którym użytkownik może wprowadzić i edytować tekst. Tekst można przypisać formatowanie znaków i akapitów i mogą zawierać osadzonych obiektów OLE. Formanty edycji wzbogaconej udostępniają interfejs programowania do formatowania tekstu. Jednak aplikacja musi implementować wszystkie składniki interfejsu użytkownika należy udostępnić użytkownikowi operacji formatowania.  
  
 `CRichEditView` przechowuje tekst i właściwości formatowania tekstu. `CRichEditDoc` przechowuje listę OLE elementy klienckie, które znajdują się w widoku. `CRichEditCntrItem` udostępnia kontener po stronie klienta elementu OLE.  
  
 Ten formant wspólne systemu Windows (i w związku z tym [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) i związanych z klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Na przykład przy użyciu elementów kontenera zaawansowanej edycji w aplikacji MFC, zobacz [WORDPAD](../../visual-cpp-samples.md) przykładowej aplikacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrich.h  
  
##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem  
 Wywołanie tej funkcji, aby utworzyć `CRichEditCntrItem` obiektu i dodaj go do dokumentu kontenera.  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *preo*  
 Wskaźnik do [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) strukturę, która opisuje element OLE. Nowe `CRichEditCntrItem` konstruowania obiektu wokół tego elementu OLE. Jeśli *preo* jest **NULL**, element klienta jest pusta.  
  
 *pContainer*  
 Wskaźnik do dokumentu kontenera, który zawiera ten element. Jeśli *pContainer* jest **NULL**, musisz jawnie wywołać [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) można dodać tego elementu klienta do dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie wykonuje żadnych inicjowania OLE.  
  
 Aby uzyskać więcej informacji, zobacz [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktury w zestawie Windows SDK.  
  
##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject  
 Wywołanie tej funkcji, aby zsynchronizować aspekt urządzenia [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318), tego `CRichEditCntrltem` do określonej przez *Otwórz*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Parametry  
 *Otwórz*  
 Odwołanie do [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) strukturę, która opisuje element OLE.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC WORDPAD](../../visual-cpp-samples.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cricheditdoc — klasa](../../mfc/reference/cricheditdoc-class.md)   
 [Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
