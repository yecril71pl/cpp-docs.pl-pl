---
title: Struktura ABC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61b5f67247b556b37cdf934f94c30947675533e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346493"
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


