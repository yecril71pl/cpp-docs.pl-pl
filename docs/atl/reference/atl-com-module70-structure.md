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
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168634"
---
# <a name="_atl_com_module70-structure"></a>Struktura _ATL_COM_MODULE70

Używany przez kod związany z modelem COM w ATL.

## <a name="syntax"></a>Składnia

```cpp
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
Rozmiar struktury używany do przechowywania wersji.

`m_hInstTypeLib`<br/>
Wystąpienie uchwytu do biblioteki typów dla tego modułu.

`m_ppAutoObjMapFirst`<br/>
Adres elementu tablicy wskazujący początek wpisów mapowania obiektów dla tego modułu.

`m_ppAutoObjMapLast`<br/>
Adres elementu tablicy wskazujący koniec wpisów mapowania obiektów dla tego modułu.

`m_csObjMap`<br/>
Sekcja krytyczna do serializacji dostępu do wpisów mapowania obiektów. Używane wewnętrznie przez ATL.

## <a name="remarks"></a>Uwagi

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) jest zdefiniowany jako element typedef _ATL_COM_MODULE70.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
