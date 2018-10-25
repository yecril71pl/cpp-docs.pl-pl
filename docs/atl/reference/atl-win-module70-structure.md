---
title: Struktura _ATL_WIN_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcb66d55f1d75d584414c0273882a5424fe72650
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064826"
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

