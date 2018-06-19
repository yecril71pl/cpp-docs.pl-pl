---
title: Struktura _ATL_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a374ee01387c576a5d1a727857badc7ef7139ad
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255469"
---
# <a name="atlmodule70-structure"></a>Struktura _ATL_MODULE70
Zawiera dane używane przez co moduł ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 `cbSize`  
 Rozmiar struktury, używane do przechowywania wersji.  
  
 `m_nLockCnt`  
 Liczba odwołanie ustalenie, jak długo modułu powinny pozostać aktywne.  
  
 **m_pTermFuncs**  
 Funkcje ścieżek, które zostały zarejestrowane ma być wywoływana podczas zamykania ATL.  
  
 **m_csStaticDataInitAndTypeInfo**  
 Używane do koordynowania dostępu do danych wewnętrznych w sytuacjach wielowątkowych.  
  
## <a name="remarks"></a>Uwagi  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) jest zdefiniowany jako element typedef z `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
## <a name="see-also"></a>Zobacz też  
  [Klasy i struktury](../../atl/reference/atl-classes.md)







