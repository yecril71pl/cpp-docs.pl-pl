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
ms.openlocfilehash: 1a648f49b0f3715fd322b1099dcebbf194f57a10
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833533"
---
# <a name="connection-point-global-functions"></a>Funkcje globalne punktu połączenia

Te funkcje zapewniają obsługę punktów połączenia i map ujścia.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Funkcja|Opis|
|-|-|
|[AtlAdvise](#atladvise)|Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.|
|[AtlUnadvise](#atlunadvise)|Kończy połączenie ustanowione przez `AtlAdvise` .|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Doradza lub nie doradza wpisom w mapie ujścia zdarzeń.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atladvise"></a><a name="atladvise"></a> AtlAdvise

Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
podczas Wskaźnik do `IUnknown` obiektu, z którym klient chce nawiązać połączenie.

*Punkt*<br/>
podczas Wskaźnik do klienta `IUnknown` .

*IID*<br/>
podczas Identyfikator GUID punktu połączenia. Zwykle jest to takie samo, jak interfejs wychodzący zarządzany przez punkt połączenia.

*Kreatora*<br/>
określoną Wskaźnik do pliku cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Obiekt sink implementuje interfejs wychodzący obsługiwany przez punkt połączenia. Klient używa pliku cookie *PDW* , aby usunąć połączenie przez przekazanie go do [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a> AtlUnadvise

Kończy połączenie ustanowione przez [AtlAdvise](#atladvise).

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
podczas Wskaźnik do `IUnknown` obiektu, z którym jest połączony klient.

*IID*<br/>
podczas Identyfikator GUID punktu połączenia. Zwykle jest to takie samo, jak interfejs wychodzący zarządzany przez punkt połączenia.

*magazynu*<br/>
podczas Plik cookie, który jednoznacznie identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a> AtlAdviseSinkMap

Wywołaj tę funkcję, aby przeprowadzić operację advise lub unadvise na wszystkich wpisach w mapie zdarzeń zbiornika obiektu.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
podczas Wskaźnik do obiektu zawierającego mapę ujścia.

*bAdvise*<br/>
podczas PRAWDA, jeśli wszystkie wpisy ujścia mają być zalecane; Wartość FALSE, jeśli wszystkie wpisy ujścia mają być niezalecane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra punktów połączenia](../../atl/reference/connection-point-macros.md)
