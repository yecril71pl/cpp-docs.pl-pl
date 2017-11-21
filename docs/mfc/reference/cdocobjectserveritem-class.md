---
title: Klasa CDocObjectServerItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs: C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f9750c1c3a108e6e007b7d8890a31a17b9a3e39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdocobjectserveritem-class"></a>Klasa CDocObjectServerItem
Implementuje zlecenia serwera OLE specjalnie z myślą o DocObject serwerów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Konstruuje `CDocObjectServerItem` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|Pobiera wskaźnik do dokumentu, który zawiera element.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|Zgłasza wyjątek, jeśli w ramach próbuje ukryć element DocObject.|  
|[CDocObjectServerItem::OnShow](#onshow)|Wywoływane przez platformę, by utworzyć DocObject elementu w miejscu aktywne. Jeśli element nie jest DocObject, wywołuje metodę [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|  
  
## <a name="remarks"></a>Uwagi  
 `CDocObjectServerItem`Definiuje funkcje Członkowskie możliwym do zastąpienia: [OnHide](#onhide), [zdarzenia](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd), i [metodzie OnShow](#onshow).  
  
 Umożliwia `CDocObjectServerItem`, zapewnić, że [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) zastąpienia w Twojej `COleServerDoc`-klasy pochodnej zwraca nową `CDocObjectServerItem` obiektu. Jeśli musisz zmienić dowolne funkcje w tego elementu, można utworzyć nowe wystąpienie klasy własne `CDocObjectServerItem`-klasy.  
  
 Aby uzyskać więcej informacji o DocObjects zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołania MFC*. Zobacz też [pierwsze kroki Internet: dokumenty aktywne](../../mfc/active-documents-on-the-internet.md) i [dokumenty aktywne](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem  
 Konstruuje `CDocObjectServerItem` obiektu.  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parametry  
 `pServerDoc`  
 Wskaźnik do dokumentu, który będzie zawierać nowy element DocObject.  
  
 `bAutoDelete`  
 Wskazuje, czy obiekt może zostać usunięta, gdy do niej łącza zostanie zwolniony. Argument ma wartość **FALSE** Jeśli `CDocObjectServerItem` obiekt jest integralną częścią danych dokumentu. Ustaw ją na **TRUE** Jeśli obiekt jest strukturą dodatkowej używany do identyfikowania zakresu w danych dokumentu, który może zostać usunięta przez platformę.  
  
##  <a name="getdocument"></a>CDocObjectServerItem::GetDocument  
 Pobiera wskaźnik do dokumentu, który zawiera element.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, który zawiera element; **NULL** Jeśli element nie jest częścią dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu dostęp do dokumentu serwera, który został przekazany jako argument [CDocObjectServerItem](#cdocobjectserveritem) konstruktora.  
  
##  <a name="onhide"></a>CDocObjectServerItem::OnHide  
 Wywoływane przez platformę, by ukryć element.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca wyjątek, jeśli element jest DocObject. Nie można ukryć aktywny element DocObject, ponieważ trwa całego widoku. Należy dezaktywować element DocObject, aby ją ukryć. Jeśli element nie jest DocObject, domyślna implementacja wywołuje [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).  
  
##  <a name="onshow"></a>CDocObjectServerItem::OnShow  
 Wywoływane przez platformę, aby nakazać aplikacji serwera, aby DocObject elementu w miejscu aktywne.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element nie jest DocObject, domyślna implementacja wywołuje [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalne przetwarzania podczas otwierania elementu DocObject.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)   
 [Klasa COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
