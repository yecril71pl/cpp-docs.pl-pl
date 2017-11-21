---
title: Klasa CD2DRoundedRect | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
dev_langs: C++
helpviewer_keywords: CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e256a20fa75a62563f6466d22448a67863ae8aeb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cd2droundedrect-class"></a>Klasa CD2DRoundedRect
Otoka dla `D2D1_ROUNDED_RECT`.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DRoundedRect::CD2DRoundedRect](#cd2droundedrect)|Przeciążone. Konstruuje `CD2DRoundedRect` obiekt z `D2D1_ROUNDED_RECT` obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `D2D1_ROUNDED_RECT`  
  
 [CD2DRoundedRect](../../mfc/reference/cd2droundedrect-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="cd2droundedrect"></a>CD2DRoundedRect::CD2DRoundedRect  
 Tworzy obiekt CD2DRoundedRect z CD2DRectF obiektu.  
  
```  
CD2DRoundedRect(
    const CD2DRectF& rectIn,  
    const CD2DSizeF& sizeRadius);  
  
CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);  
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```  
  
### <a name="parameters"></a>Parametry  
 `rectIn`  
 Prostokąt źródła  
  
 `sizeRadius`  
 rozmiar RADIUS  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
