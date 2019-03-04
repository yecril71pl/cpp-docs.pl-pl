---
title: _ATL_BASE_MODULE70 Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 4fddd4b3af6155d0663b9c01edfab4fcf4a60426
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261464"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 Structure

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

`cbSize`<br/>
Rozmiar struktury, używane do obsługi wersji.

`m_hInst`<br/>
`hInstance` Dla tego modułu (plik exe lub dll).

`m_hInstResource`<br/>
Dojście do zasobu wystąpienie domyślne.

`m_bNT5orWin98`<br/>
Informacje o wersji systemu operacyjnego. Używane wewnętrznie przez ATL.

`dwAtlBuildVer`<br/>
Przechowuje wersję ATL. Obecnie 0x0700.

`pguidVer`<br/>
ATL wewnętrzny identyfikator GUID.

`m_csResource`<br/>
Używane do synchronizowania dostępu do `m_rgResourceInstance` tablicy. Używane wewnętrznie przez ATL.

`m_rgResourceInstance`<br/>
Tablica używanych do wyszukiwania zasobów we wszystkich wystąpieniach zasobów, których ATL zdaje sobie sprawę. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) jest zdefiniowany jako element typedef _ATL_BASE_MODULE70.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
