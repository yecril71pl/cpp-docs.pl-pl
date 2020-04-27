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
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168556"
---
# <a name="_atl_win_module70-structure"></a>Struktura _ATL_WIN_MODULE70

Używane przez kod okna w ATL.

## <a name="syntax"></a>Składnia

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Elementy członkowskie

`cbSize`<br/>
Rozmiar struktury używany do przechowywania wersji.

`m_csWindowCreate`<br/>
Służy do serializacji dostępu do kodu rejestracji okna. Używane wewnętrznie przez ATL.

`m_pCreateWndList`<br/>
Służy do wiązania systemu Windows z obiektami. Używane wewnętrznie przez ATL.

`m_rgWindowClassAtoms`<br/>
Służy do śledzenia rejestracji klas okien, aby można je było prawidłowo wyrejestrować po zakończeniu. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) jest zdefiniowany jako element typedef elementu `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
