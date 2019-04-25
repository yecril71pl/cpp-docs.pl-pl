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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278271"
---
# <a name="connection-point-global-functions"></a>Funkcje globalne punktu połączenia

Te funkcje umożliwiają punkty połączenia i ujście mapy.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlAdvise](#atladvise)|Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.|
|[AtlUnadvise](#atlunadvise)|Przerywa połączenie ustanowione przez `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Z informacją o tym, lub unadvises wpisy na mapie obiektu sink zdarzenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

Tworzy połączenie między punktem połączenia obiektu a zbiornikiem klienta.

> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
[in] Wskaźnik do `IUnknown` obiektu klient chce się nawiązać połączenia z.

*pUnk*<br/>
[in] Wskaźnik do klienta `IUnknown`.

*IID*<br/>
[in] Identyfikator GUID punktu połączenia. Zazwyczaj jest taka sama jak interfejsu wychodzącego zarządzane przez punkt połączenia.

*PDW*<br/>
[out] Wskaźnik do pliku cookie, który unikatowo identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Obiekt sink implementuje interfejsu wychodzącego obsługiwane przez punkt połączenia. Klient używa *pdw* plików cookie, aby usunąć połączenie przez przekazanie jej do [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

Przerywa połączenie ustanowione przez [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parametry

*pUnkCP*<br/>
[in] Wskaźnik do `IUnknown` obiektu, który klient jest połączony z.

*IID*<br/>
[in] Identyfikator GUID punktu połączenia. Zazwyczaj jest taka sama jak interfejsu wychodzącego zarządzane przez punkt połączenia.

*dw*<br/>
[in] Plik cookie, który unikatowo identyfikuje połączenie.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

Wywołaj tę funkcję, aby przeprowadzić operację advise lub unadvise na wszystkich wpisach w mapie zdarzeń zbiornika obiektu.

> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parametry

*pT*<br/>
[in] Wskaźnik do obiektu zawierającego mapy ujścia.

*bAdvise*<br/>
[in] Wartość TRUE, jeśli wszystkie wpisy ujścia zaleceniem; Wartość FALSE, jeśli mają być unadvised wszystkie wpisy ujścia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)<br/>
[Makra punktów połączenia](../../atl/reference/connection-point-macros.md)
