---
title: Struktura ABC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABC
dev_langs: C++
helpviewer_keywords: ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ba8add08fcd5ff3d7343477aafa7d910885b0b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="abc-structure"></a>Struktura ABC
**ABC** struktura zawiera szerokość znaku czcionki TrueType.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>Parametry  
 *abcA*  
 Określa odstępy A znaku. A jest odległość do dodania do bieżącego położenia przed narysowaniem znak symbolu.  
  
 *abcB*  
 Określa odstępy B znaku. B jest szerokość narysowanego część znak symbolu.  
  
 *abcC*  
 Określa odstępy C znaku. C jest odległość do dodania do bieżącego położenia zapewnienie biały znak z prawej strony symbolu znaków.  
  
## <a name="remarks"></a>Uwagi  
 Łączna szerokość znaku jest sumą spacje A, B i C. A lub miejsca C może być ujemna underhangs lub znacznego udziału.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


