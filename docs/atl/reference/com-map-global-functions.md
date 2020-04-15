---
title: Funkcje globalne map com map
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326696"
---
# <a name="com-map-global-functions"></a>Funkcje globalne map com map

Te funkcje zapewniają `IUnknown` obsługę implementacji mapy COM.

|||
|-|-|
|[AtlInternalQueryInterface (AtlInternalQueryInterface)](#atlinternalqueryinterface)|Delegaci `IUnknown` do obiektu nieagregowanego.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje wydajny kod do porównywania interfejsów z . `IUnknown`|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface (AtlInternalQueryInterface)

Pobiera wskaźnik do żądanego interfejsu.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pThis*<br/>
[w] Wskaźnik do obiektu zawierającego mapę COM interfejsów narażonych na `QueryInterface`działanie .

*pEntries (PEntries)*<br/>
[w] Tablica `_ATL_INTMAP_ENTRY` struktur, które uzyskują dostęp do mapy dostępnych interfejsów.

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu określonego w *iid*lub NULL, jeśli nie zostanie znaleziony interfejs.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlInternalQueryInterface`obsługuje tylko interfejsy w tabeli mapy COM. Jeśli obiekt jest agregowany, `AtlInternalQueryInterface` nie przekazuje do zewnętrznej nieznanej. Interfejsy można wprowadzić w tabeli mapy COM z [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) makra lub jednym z jego wariantów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown

Wywołanie tej funkcji, dla specjalnego `IUnknown`przypadku badania dla .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parametry

*rguid1*<br/>
[w] Identyfikator GUID do `IID_IUnknown`porównania z programem .

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra map COM](../../atl/reference/com-map-macros.md)
