---
title: Struktura _ATL_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: bf733a10a0be53eafb634c645dad6a4b58b8206d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438847"
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

`cbSize`<br/>
Rozmiar struktury, używane do obsługi wersji.

`m_nLockCnt`<br/>
Aby określić, jak długo moduł powinien pozostaną aktywne liczbę odwołań.

`m_pTermFuncs`<br/>
Funkcje ścieżki, które zostały zarejestrowane wywoływana, gdy zamyka ATL.

`m_csStaticDataInitAndTypeInfo`<br/>
Używane do koordynowania dostępu do danych wewnętrznych w sytuacjach wielowątkowych.

## <a name="remarks"></a>Uwagi

[_ATL_MODULE](atl-typedefs.md#_atl_module) jest zdefiniowany jako element typedef dla `_ATL_MODULE70`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)

