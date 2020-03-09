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
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864405"
---
# <a name="connection-point-global-functions"></a>Funkcje globalne punktu połączenia

Te funkcje zapewniają obsługę punktów połączenia i map ujścia.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|||
|-|-|
|[AtlAdvise](#atladvise)|Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.|
|[AtlUnadvise](#atlunadvise)|Kończy połączenie ustanowione za pomocą `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Doradza lub nie doradza wpisom w mapie ujścia zdarzeń.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="atladvise"></a>AtlAdvise

Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
podczas Wskaźnik do `IUnknown`klienta.

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

##  <a name="atlunadvise"></a>AtlUnadvise

Kończy połączenie ustanowione przez [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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

##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Wywołaj tę funkcję, aby przeprowadzić operację advise lub unadvise na wszystkich wpisach w mapie zdarzeń zbiornika obiektu.

> [!IMPORTANT]
>  Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
