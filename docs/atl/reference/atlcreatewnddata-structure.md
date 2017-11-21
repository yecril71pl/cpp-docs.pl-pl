---
title: Struktura _AtlCreateWndData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs: C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a5b0811e88188bb29ef3153f739804cbdac66083
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atlcreatewnddata-structure"></a>Struktura _AtlCreateWndData
Ta struktura zawiera dane wystąpienia klasy w kodzie okien w ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 **m_pThis**  
 **To** wskaźnik został użyty do uzyskania dostępu do wystąpienia klasy w procedury okna.  
  
 `m_dwThreadID`  
 Identyfikator wątku bieżącego wystąpienia klasy.  
  
 **m_pNext**  
 Wskaźnik do następnego `_AtlCreateWndData` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)





