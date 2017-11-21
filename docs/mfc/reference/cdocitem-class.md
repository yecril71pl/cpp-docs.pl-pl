---
title: Klasa CDocItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs: C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d8ca7968011061b36fe0b0e54bea457ee40c431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[CDocItem::GetDocument](#getdocument)|Zwraca dokument, który zawiera element.|  
|[CDocItem::IsBlank](#isblank)|Określa, czy element zawiera wszystkie informacje.|  
  
## <a name="remarks"></a>Uwagi  
 `CDocItem`obiekty są używane do reprezentowania elementy OLE w dokumentach klienta i serwera.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="getdocument"></a>CDocItem::GetDocument  
 Wywołanie tej funkcji, aby pobrać dokument, który zawiera element.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, który zawiera element; **NULL**, jeśli element nie jest częścią dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przesłonięte w klasach pochodnych [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md), zwracany jest wskaźnik do albo [COleDocument](../../mfc/reference/coledocument-class.md), [ COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), lub [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) obiektu.  
  
##  <a name="isblank"></a>CDocItem::IsBlank  
 Wywoływane przez platformę, gdy wystąpi domyślnej serializacji.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli element nie zawiera żadnych informacji; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `CDocItem` obiekty nie są puste. [COleClientItem](../../mfc/reference/coleclientitem-class.md) obiektów czasami są puste, ponieważ ich pochodzi bezpośrednio z `CDocItem`. Jednak [COleServerItem](../../mfc/reference/coleserveritem-class.md) obiektów zawsze są puste. Domyślnie w aplikacji OLE zawierających `COleClientItem` obiektów, które nie zawierają x ani y zakresie są serializowane. Polega to na zwracanie **TRUE** z zastępująca `IsBlank` Jeśli element nie ma x ani y zakresu.  
  
 Należy przesłonić tę funkcję, aby zaimplementować inne akcje podczas serializacji.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDocument](../../mfc/reference/coledocument-class.md)   
 [Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)
