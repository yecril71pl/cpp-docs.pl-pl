---
title: Struktura XFORM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: XFORM
dev_langs: C++
helpviewer_keywords: XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f6f7121b5cc93c3f8f6f34f22d16cef888bbf15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="xform-structure"></a>Struktura XFORM
`XFORM` Struktury ma następujący format:  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>Uwagi  
 `XFORM` Struktury określa miejsce na świecie do przekształcania miejsca strony. **EDx** i **eDy** elementów członkowskich określają odpowiednio składniki tłumaczenia poziomie i w pionie. W poniższej tabeli przedstawiono, jak są używane inne elementy członkowskie, w zależności od operacji:  
  
|Operacja|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|Cosinus kąta obrotu|Sinus kąta obrotu|Ujemna sinus kąta obrotu|Cosinus kąta obrotu|  
|**Skalowanie**|Skalowania składowej poziomej|Nothing|Nothing|Skalowania składowej pionowej|  
|**Zmienianie**|Nothing|Stała proporcjonalności pozioma|Stała proporcjonalności pionowe|Nothing|  
|**Odbicie**|Składnik poziome odbicia|Nothing|Nothing|Składnik pionowego odbicia|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

