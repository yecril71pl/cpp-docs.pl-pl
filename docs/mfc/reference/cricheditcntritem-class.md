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
ms.openlocfilehash: 2a0566ef5eead5950f2b4de1f6e1a220f79bcfbe
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849330"
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
 *preo*  
 Wskaźnik do [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktury, które opisują elementu OLE. Nowy `CRichEditCntrItem` obiekt jest konstruowany wokół tego elementu OLE. Jeśli *preo* ma wartość NULL, element klienta jest pusty.  
  
 *pContainer*  
 Wskaźnik do dokumentu kontenera, który będzie zawierać tego elementu. Jeśli *element pContainer* ma wartość NULL, należy jawnie wywołać [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) można dodać tego elementu klienta do dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie wykonuje żadnych Inicjalizacja OLE.  
  
 Aby uzyskać więcej informacji, zobacz [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktury w zestawie Windows SDK.  
  
##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject  
 Wywołaj tę funkcję, aby zsynchronizować aspektu urządzenia [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318), to `CRichEditCntrltem` do określonej przez *Otwórz*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Parametry  
 *Otwórz*  
 Odwołanie do [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) struktury, które opisują elementu OLE.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC WORDPAD](../../visual-cpp-samples.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)   
 [Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
