---
title: Dhtmlurleventmapentry — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee629d9dcffc80ce20306989cad72d466722af87
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123334"
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
 *szUrl*  
 Adres URL.  
  
 *pEventMap*  
 Mapa zdarzeń skojarzone z adresem URL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdhtml.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

