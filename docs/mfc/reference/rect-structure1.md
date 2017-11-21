---
title: RECT Structure1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs: C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d3a33330ace97db19521362384356b58a6c8dca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Klasa CRect](../../atl-mfc-shared/reference/crect-class.md)
