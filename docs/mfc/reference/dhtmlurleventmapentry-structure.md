---
title: "Dhtmlurleventmapentry — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea92126cf57bf122ebd720d6bd8e6f12a98f65ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry — Struktura
`DHtmlUrlEventMapEntry` Struktura zapewnia obsługę mapy zdarzeń wielu adresu URL.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct DHtmlUrlEventMapEntry  
{  
LPCTSTR szUrl;  
const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `szUrl`  
 Adres URL.  
  
 *pEventMap*  
 Mapa zdarzeń skojarzone z adresem URL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdhtml.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

