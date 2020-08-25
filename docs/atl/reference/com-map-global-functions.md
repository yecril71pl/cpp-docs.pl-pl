---
title: Globalne funkcje mapowania modelu COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: adf4e06eb46aed74d08071dccce1db549ca31226
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833598"
---
# <a name="com-map-global-functions"></a>Globalne funkcje mapowania modelu COM

Te funkcje zapewniają obsługę implementacji mapowań COM `IUnknown` .

|Funkcja|Opis|
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje do `IUnknown` obiektu niezagregowanego.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje wydajny kod służący do porównywania interfejsów z `IUnknown` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a> AtlInternalQueryInterface

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
podczas Wskaźnik do obiektu, który zawiera mapę COM interfejsów dostępnych dla `QueryInterface` .

*pEntries*<br/>
podczas Tablica `_ATL_INTMAP_ENTRY` struktur, które uzyskują dostęp do mapy dostępnych interfejsów.

*IID*<br/>
podczas Identyfikator GUID żądanego interfejsu.

*ppvObject*<br/>
określoną Wskaźnik do wskaźnika interfejsu określonego w *identyfikatorze IID*lub wartość null, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

`AtlInternalQueryInterface` obsługuje tylko interfejsy w tabeli mapy COM. Jeśli obiekt jest zagregowany, `AtlInternalQueryInterface` nie jest delegowany do nieznanego obiektu zewnętrznego. Możesz wprowadzić interfejsy w tabeli mapy modelu COM z makrem [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) lub jednym z jego wariantów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a> InlineIsEqualIUnknown

Wywołaj tę funkcję, w przypadku specjalnego przypadku testowania dla `IUnknown` .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parametry

*rguid1*<br/>
podczas Identyfikator GUID, do którego ma zostać wykonane porównanie `IID_IUnknown` .

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra mapy modelu COM](../../atl/reference/com-map-macros.md)
