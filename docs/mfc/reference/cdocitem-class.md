---
title: Klasa CDocItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c30418f886cd791a7119367c5ddbccc19003fa
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335584"
---
# <a name="cdocitem-class"></a>Klasa CDocItem
Klasa bazowa dla elementów dokumentu, które są składnikami danych dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|Zwraca dokument, który zawiera element.|  
|[CDocItem::IsBlank](#isblank)|Określa, czy element zawiera wszystkie informacje.|  
  
## <a name="remarks"></a>Uwagi  
 `CDocItem` obiekty są używane do reprezentowania elementy OLE w dokumentach klienta i serwera.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="getdocument"></a>  CDocItem::GetDocument  
 Wywołaj tę funkcję, aby pobrać dokument, który zawiera element.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, który zawiera element; Wartość NULL, jeśli element nie jest częścią dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja zostanie zastąpiona w klasach pochodnych [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md), zwraca wskaźnik do jednego [COleDocument](../../mfc/reference/coledocument-class.md), [ COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), lub [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) obiektu.  
  
##  <a name="isblank"></a>  CDocItem::IsBlank  
 Metoda wywoływana przez platformę podczas serializacji domyślny.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli element nie zawiera żadnych informacji; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CDocItem` obiekty nie są puste. [COleClientItem](../../mfc/reference/coleclientitem-class.md) obiekty czasami są puste, ponieważ mogą dziedziczyć bezpośrednio `CDocItem`. Jednak [COleServerItem](../../mfc/reference/coleserveritem-class.md) obiekty są zawsze puste. Domyślnie w aplikacji OLE zawierających `COleClientItem` obiektów, które mają nie x lub y zakresu są serializowane. Odbywa się, zwracając wartość TRUE z zastąpieniem `IsBlank` Jeśli element nie ma x lub y zakresu.  
  
 Należy przesłonić tę funkcję, aby wdrożyć inne akcje podczas serializacji.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDocument](../../mfc/reference/coledocument-class.md)   
 [Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)
