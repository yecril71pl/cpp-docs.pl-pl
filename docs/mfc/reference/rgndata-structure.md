---
title: Struktura RGNDATA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RGNDATA
dev_langs: C++
helpviewer_keywords: RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f637dfd76ba293454c7a5c51b12ad60926280a72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rgndata-structure"></a>Struktura RGNDATA
`RGNDATA` Struktura zawiera nagłówek i Tablica prostokąty tworzące region. Te prostokąty posortowane od góry do dołu w lewej do prawej, nie mogą się pokrywać.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>Parametry  
 *rdh*  
 Określa [RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941) struktury. (Aby uzyskać więcej informacji dotyczących tej struktury, zobacz zestaw Windows SDK). Elementy członkowskie tej struktury określenie typu regionu (czy jest prostokątne lub trapezoidal), liczba prostokąty wchodzące w skład regionu, rozmiar buforu, który zawiera struktury prostokąt i tak dalej.  
  
 `Buffer`  
 Określa dowolnego rozmiaru buforu, który zawiera [RECT](../../mfc/reference/rect-structure1.md) struktury wchodzące w skład regionu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

