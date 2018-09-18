---
title: Struktura _ATL_COM_MODULE70 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cfa52749f6789ef8bfe65f9bdcdf5238923216f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019385"
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

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../../atl/reference/atl-classes.md)

