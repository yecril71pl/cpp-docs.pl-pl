---
title: RECT Structure1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b61c794b8fa383eeea62459a5a83948ef2efe10
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372596"
---
# <a name="rect-structure1"></a>RECT Structure1
`RECT` Struktury definiuje współrzędne górnego lewego i prawego dolnego rogu prostokąta.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `left`  
 Określa współrzędną x górnego lewego rogu prostokąta.  
  
 `top`  
 Określa współrzędną y górnego lewego rogu prostokąta.  
  
 `right`  
 Określa współrzędną x prawym dolnym rogu prostokąta.  
  
 `bottom`  
 Określa współrzędną y prawego dolnego rogu prostokąta.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** windef.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)
