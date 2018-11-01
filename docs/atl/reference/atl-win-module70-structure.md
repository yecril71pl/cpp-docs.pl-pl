---
title: Struktura _ATL_WIN_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 4f1718c76d21f2e13b36c29db785fe989ff6108e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482524"
---
# <a name="atlwinmodule70-structure"></a>Struktura _ATL_WIN_MODULE70

Używane przez kod obsługi okien w ATL.

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

`cbSize`<br/>
Rozmiar struktury, używane do obsługi wersji.

`m_csWindowCreate`<br/>
Służy do serializacji dostęp do okna kodu rejestracyjnego. Używane wewnętrznie przez ATL.

`m_pCreateWndList`<br/>
Używane do powiązania systemu windows w nich obiekty. Używane wewnętrznie przez ATL.

`m_rgWindowClassAtoms`<br/>
Używane do śledzenia rejestracje klasy okna, tak aby mogły być prawidłowo wyrejestrować po zakończeniu. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) jest zdefiniowany jako element typedef dla `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)

