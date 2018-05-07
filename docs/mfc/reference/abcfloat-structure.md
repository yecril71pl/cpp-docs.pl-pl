---
title: Struktura ABCFLOAT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5be39336f3da839dc9b1c7be6a64db54b59f99bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

