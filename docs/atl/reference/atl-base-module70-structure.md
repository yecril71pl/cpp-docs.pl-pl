---
title: Struktura _ATL_BASE_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7218d7fc8886cffdcce13f09a682fdc635f84f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759931"
---
# <a name="atlbasemodule70-structure"></a>Struktura _ATL_BASE_MODULE70

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

`cbSize`  
Rozmiar struktury, używane do obsługi wersji.

`m_hInst`  
`hInstance` Dla tego modułu (plik exe lub dll).

`m_hInstResource`  
Dojście do zasobu wystąpienie domyślne.

`m_bNT5orWin98`  
Informacje o wersji systemu operacyjnego. Używane wewnętrznie przez ATL.

`dwAtlBuildVer`  
Przechowuje wersję ATL. Obecnie 0x0700.

`pguidVer`  
ATL wewnętrzny identyfikator GUID.

`m_csResource`  
Używane do synchronizowania dostępu do `m_rgResourceInstance` tablicy. Używane wewnętrznie przez ATL.

`m_rgResourceInstance`  
Tablica używanych do wyszukiwania zasobów we wszystkich wystąpieniach zasobów, których ATL zdaje sobie sprawę. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) jest zdefiniowany jako element typedef _ATL_BASE_MODULE70.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)

