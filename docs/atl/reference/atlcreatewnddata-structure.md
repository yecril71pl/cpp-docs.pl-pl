---
title: Struktura _AtlCreateWndData | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66388c12def72a9da5b5aeb7e4713ca61c23a6e0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
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
 [Klasy i struktury](../../atl/reference/atl-classes.md)





