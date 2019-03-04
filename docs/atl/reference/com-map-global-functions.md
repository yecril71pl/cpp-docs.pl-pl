---
title: Funkcje globalne mapy interfejsu COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: 75d081674fa4b63e66f1296834d3de305665ab9a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271622"
---
# <a name="com-map-global-functions"></a>Funkcje globalne mapy interfejsu COM

Te funkcje umożliwiają mapy interfejsu COM `IUnknown` implementacji.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Deleguje do `IUnknown` nieagregowane obiektu.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generuje kod wydajne porównywania interfejsów względem `IUnknown`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

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
[in] Wskaźnik do obiektu, która zawiera mapę COM, interfejsów narażonych na `QueryInterface`.

*pEntries*<br/>
[in] Tablica `_ATL_INTMAP_ENTRY` struktury, do których dostęp mapę dostępnych interfejsów.

*IID*<br/>
[in] Identyfikator GUID interfejsu żądanej.

*ppvObject*<br/>
[out] Wskaźnik do wskaźnika interfejsu określonego w *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

`AtlInternalQueryInterface` obsługuje tylko interfejsów COM tabeli mapy. Jeśli obiekt jest zagregowany, `AtlInternalQueryInterface` nie delegować do zewnętrznego nieznany. Możesz wprowadzić interfejsy do tabeli mapy COM za pomocą makra [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) lub jedna z jej wariantów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

Wywołaj tę funkcję w specjalnym przypadku sprawdzania pod kątem `IUnknown`.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parametry

*rguid1*<br/>
[in] Identyfikator GUID do porównania z `IID_IUnknown`.

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra mapy modelu COM](../../atl/reference/com-map-macros.md)
