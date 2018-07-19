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
ms.openlocfilehash: 2c9aac181edb12df8904a2bc6d891d59c0067ecc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339322"
---
# <a name="abc-structure"></a>Struktura ABC
`ABC` Struktura zawiera szerokość znaku czcionki TrueType.  
  
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
 Określa odstępy A znaku. Element jest odległość do dodania do bieżącego położenia przed narysowaniem symbol znaku.  
  
 *abcB*  
 Określa odstępy B znaku. Odstępy B jest szerokość rysowane część symbol znaku.  
  
 *abcC*  
 Określa odstępy C znaku. Odstępy C jest odległość, aby dodać do aktualnej pozycji, aby zapewnić biały znak z prawej strony symbolu znaku.  
  
## <a name="remarks"></a>Uwagi  
 Łączna szerokość znaku jest sumą A, B i C miejsca do magazynowania. Element lub miejsca C może być ujemna na wskazywać underhangs lub znacznego udziału.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** wingdi.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


