---
title: Struktura _ATL_COM_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs: C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a269820c5a0965553989bc57d7c239aa95e527ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atlcommodule70-structure"></a>Struktura _ATL_COM_MODULE70
Używany przez kod związanych z modelu COM w ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 `cbSize`  
 Rozmiar struktury, używane do przechowywania wersji.  
  
 `m_hInstTypeLib`  
 Wystąpienia dojścia do biblioteki typów dla tego modułu.  
  
 **m_ppAutoObjMapFirst**  
 Adresu elementu tablicy, wskazując na początku wpisów map obiekt dla tego modułu.  
  
 **m_ppAutoObjMapLast**  
 Adresu elementu tablicy, co oznacza koniec wpisów map obiekt dla tego modułu.  
  
 `m_csObjMap`  
 Sekcja krytyczna do serializacji dostęp do wpisów map obiekt. Używana wewnętrznie przez ATL.  
  
## <a name="remarks"></a>Uwagi  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) jest zdefiniowany jako element typedef z `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)





