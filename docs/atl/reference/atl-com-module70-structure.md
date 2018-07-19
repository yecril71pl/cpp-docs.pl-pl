---
title: Struktura _ATL_COM_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a3140a0013d284b9145029575418054af22c65e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883716"
---
# <a name="atlcommodule70-structure"></a>Struktura _ATL_COM_MODULE70
Używane przez kod związane z modelu COM w ATL.  
  
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
 Rozmiar struktury, używane do obsługi wersji.  
  
 `m_hInstTypeLib`  
 Wystąpienie uchwyt do biblioteki typów dla tego modułu.  
  
 `m_ppAutoObjMapFirst`  
 Adres elementu tablicy, wskazując początku wpisy mapy obiektu dla tego modułu.  
  
 `m_ppAutoObjMapLast`  
 Adres elementu tablicy, co oznacza koniec wpisy mapy obiektu dla tego modułu.  
  
 `m_csObjMap`  
 Sekcję krytyczną serializować dostęp do wpisy mapy obiektu. Używane wewnętrznie przez ATL.  
  
## <a name="remarks"></a>Uwagi  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) jest zdefiniowany jako element typedef _ATL_COM_MODULE70.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy i struktury](../../atl/reference/atl-classes.md)





