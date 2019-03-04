---
title: Struktura _ATL_COM_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c6361fc5374ed732cd9ccbfbbd1d3d1c2fc8f1f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261287"
---
# <a name="atlcommodule70-structure"></a>Struktura _ATL_COM_MODULE70

Używane przez kod związane z modelu COM w ATL.

## <a name="syntax"></a>Składnia

```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Elementy członkowskie

`cbSize`<br/>
Rozmiar struktury, używane do obsługi wersji.

`m_hInstTypeLib`<br/>
Wystąpienie uchwyt do biblioteki typów dla tego modułu.

`m_ppAutoObjMapFirst`<br/>
Adres elementu tablicy, wskazując początku wpisy mapy obiektu dla tego modułu.

`m_ppAutoObjMapLast`<br/>
Adres elementu tablicy, co oznacza koniec wpisy mapy obiektu dla tego modułu.

`m_csObjMap`<br/>
Sekcję krytyczną serializować dostęp do wpisy mapy obiektu. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) jest zdefiniowany jako element typedef _ATL_COM_MODULE70.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
