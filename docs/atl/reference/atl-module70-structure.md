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
ms.openlocfilehash: e7afe6867f359b334654f58aad39ad7f143dd428
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764894"
---
# <a name="atlmodule70-structure"></a>Struktura _ATL_MODULE70

Zawiera dane używane przez każdy moduł ATL.

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
Rozmiar struktury, używane do obsługi wersji.

`m_nLockCnt`  
Aby określić, jak długo moduł powinien pozostaną aktywne liczbę odwołań.

`m_pTermFuncs`  
Funkcje ścieżki, które zostały zarejestrowane wywoływana, gdy zamyka ATL.

`m_csStaticDataInitAndTypeInfo`  
Używane do koordynowania dostępu do danych wewnętrznych w sytuacjach wielowątkowych.

## <a name="remarks"></a>Uwagi

[_ATL_MODULE](atl-typedefs.md#_atl_module) jest zdefiniowany jako element typedef dla `_ATL_MODULE70`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)

