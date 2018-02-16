---
title: Struktura _ATL_BASE_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f711621188cffb739fe6895af3b222993c84576c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="atlbasemodule70-structure"></a>Struktura _ATL_BASE_MODULE70
Używane przez dowolny projekt, który używa ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 `cbSize`  
 Rozmiar struktury, używane do przechowywania wersji.  
  
 `m_hInst`  
 **Wystąpienie hInstance** dla tego modułu (plik exe lub dll).  
  
 `m_hInstResource`  
 Dojście do zasobu wystąpienia domyślnego.  
  
 **m_bNT5orWin98**  
 Informacje o wersji systemu operacyjnego. Używana wewnętrznie przez ATL.  
  
 **dwAtlBuildVer**  
 Przechowuje wersji ATL. Obecnie 0x0700.  
  
 **pguidVer**  
 Wewnętrzny identyfikator GUID w ATL.  
  
 **m_csResource**  
 Używane do dostępu do synchronizowania **m_rgResourceInstance** tablicy. Używana wewnętrznie przez ATL.  
  
 **m_rgResourceInstance**  
 Służy do wyszukiwania zasobów we wszystkich wystąpieniach zasobów, których ATL jest świadome tablicy. Używana wewnętrznie przez ATL.  
  
## <a name="remarks"></a>Uwagi  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) jest zdefiniowany jako element typedef z `_ATL_BASE_MODULE70`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)





