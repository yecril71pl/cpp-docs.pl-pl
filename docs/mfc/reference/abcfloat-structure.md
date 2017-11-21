---
title: Struktura ABCFLOAT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABCFLOAT
dev_langs: C++
helpviewer_keywords: ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 983439d773a7ded59e09c1385bce4febc9979ef6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="abcfloat-structure"></a>Struktura ABCFLOAT
`ABCFLOAT` Struktura zawiera A, B i C szerokość znaków czcionki.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *abcfA*  
 Określa odstępy A znaku. A jest odległość do dodania do bieżącego położenia przed narysowaniem znak symbolu.  
  
 *abcfB*  
 Określa odstępy B znaku. B jest szerokość narysowanego część znak symbolu.  
  
 *abcfC*  
 Określa odstępy C znaku. C jest odległość do dodania do bieżącego położenia zapewnienie biały znak z prawej strony symbolu znaków.  
  
## <a name="remarks"></a>Uwagi  
 Szerokość A, B i C są mierzone wzdłuż linii bazowej czcionki. Przyrost znaków (łączna szerokość) znaku jest sumą spacje A, B i C. A lub miejsca C może być ujemna underhangs lub znacznego udziału.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

