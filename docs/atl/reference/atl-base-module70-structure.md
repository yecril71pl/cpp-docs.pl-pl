---
title: Struktura _ATL_BASE_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168647"
---
# <a name="_atl_base_module70-structure"></a>Struktura _ATL_BASE_MODULE70

Używane przez dowolny projekt, który używa ATL.

## <a name="syntax"></a>Składnia

```cpp
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
Rozmiar struktury używany do przechowywania wersji.

`m_hInst`<br/>
`hInstance` Dla tego modułu (exe lub dll).

`m_hInstResource`<br/>
Domyślne dojście do zasobu wystąpienia.

`m_bNT5orWin98`<br/>
Informacje o wersji systemu operacyjnego. Używane wewnętrznie przez ATL.

`dwAtlBuildVer`<br/>
Przechowuje wersję biblioteki ATL. Obecnie 0x0700.

`pguidVer`<br/>
Wewnętrzny identyfikator GUID biblioteki ATL.

`m_csResource`<br/>
Służy do synchronizowania dostępu do `m_rgResourceInstance` tablicy. Używane wewnętrznie przez ATL.

`m_rgResourceInstance`<br/>
Tablica służąca do wyszukiwania zasobów we wszystkich wystąpieniach zasobów, dla których jest rozróżniana ATL. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) jest zdefiniowany jako element typedef _ATL_BASE_MODULE70.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
