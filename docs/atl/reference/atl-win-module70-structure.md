---
title: Struktura _ATL_WIN_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d284f18005b470f80cc911a24ec2c813715a0ca4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="atlwinmodule70-structure"></a>Struktura _ATL_WIN_MODULE70
Używany przez kod okien w ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize; 
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 `cbSize`  
 Rozmiar struktury, używane do przechowywania wersji.  
  
 `m_csWindowCreate`  
 Umożliwia dostęp do okna rejestracji kodu serializacji. Używana wewnętrznie przez ATL.  
  
 **m_pCreateWndList**  
 Używane dla wiązania systemu windows w nich obiekty. Używana wewnętrznie przez ATL.  
  
 **m_rgWindowClassAtoms**  
 Używane do śledzenia rejestracji klasy okna, tak aby mogły być poprawnie wyrejestrować po zakończeniu. Używana wewnętrznie przez ATL.  
  
## <a name="remarks"></a>Uwagi  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) jest zdefiniowany jako element typedef z `_ATL_WIN_MODULE70`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)





