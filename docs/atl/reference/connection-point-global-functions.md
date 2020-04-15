---
title: Funkcje globalne punktu połączenia
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331533"
---
# <a name="connection-point-global-functions"></a>Funkcje globalne punktu połączenia

Funkcje te zapewniają obsługę punktów połączenia i map ujścia.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlAdvise (AtlAdvise)](#atladvise)|Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.|
|[AtlUnadvise ( AtlUnadvise )](#atlunadvise)|Kończy połączenie nawiązane `AtlAdvise`za pośrednictwem .|
|[Mapa AtlAdviseSink](#atladvisesinkmap)|Doradza lub unadvises wpisów na mapie sink zdarzenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>AtlAdvise (AtlAdvise)

Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP (protokół z punktu/ wyt*<br/>
[w] Wskaźnik do `IUnknown` obiektu, z który klient chce się połączyć.

*Punk*<br/>
[w] Wskaźnik do klienta `IUnknown`.

*Iid*<br/>
[w] Identyfikator GUID punktu połączenia. Zazwyczaj jest to taka sama jak interfejs wychodzący zarządzany przez punkt połączenia.

*Pdw*<br/>
[na zewnątrz] Wskaźnik do pliku cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Unik implementuje interfejs wychodzący obsługiwany przez punkt połączenia. Klient używa pliku cookie *pdw,* aby usunąć połączenie, przekazując je do [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise ( AtlUnadvise )

Kończy połączenie nawiązane za pośrednictwem [AtlAdvise](#atladvise).

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP (protokół z punktu/ wyt*<br/>
[w] Wskaźnik do `IUnknown` obiektu, z który jest połączony klient.

*Iid*<br/>
[w] Identyfikator GUID punktu połączenia. Zazwyczaj jest to taka sama jak interfejs wychodzący zarządzany przez punkt połączenia.

*Dw*<br/>
[w] Plik cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>Mapa AtlAdviseSink

Wywołaj tę funkcję, aby przeprowadzić operację advise lub unadvise na wszystkich wpisach w mapie zdarzeń zbiornika obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[w] Wskaźnik do obiektu zawierającego mapę ujścia.

*bAdvise*<br/>
[w] PRAWDA, jeśli wszystkie wpisy zlewu mają być zalecane; FALSE, jeśli wszystkie wpisy ujścia mają być unadvised.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra punktu połączenia](../../atl/reference/connection-point-macros.md)
