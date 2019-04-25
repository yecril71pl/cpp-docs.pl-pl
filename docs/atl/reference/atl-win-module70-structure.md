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
ms.openlocfilehash: 0b636d328852daf821269230aae443cef084578b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260756"
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

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
