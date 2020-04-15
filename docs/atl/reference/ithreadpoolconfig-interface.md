---
title: Interfejs IThreadPoolConfig
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326360"
---
# <a name="ithreadpoolconfig-interface"></a>Interfejs IThreadPoolConfig

Ten interfejs zawiera metody konfigurowania puli wątków.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetSize](#getsize)|Wywołanie tej metody, aby uzyskać liczbę wątków w puli.|
|[GetTimeout (Czas realizacji)](#gettimeout)|Wywołanie tej metody, aby uzyskać maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.|
|[Setsize](#setsize)|Wywołanie tej metody, aby ustawić liczbę wątków w puli.|
|[Settimeout](#settimeout)|Wywołanie tej metody, aby ustawić maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest zaimplementowany przez [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize

Wywołanie tej metody, aby uzyskać liczbę wątków w puli.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parametry

*pnNumCięty*<br/>
[na zewnątrz] Adres zmiennej, która po sukcesie odbiera liczbę wątków w puli.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout

Wywołanie tej metody, aby uzyskać maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[na zewnątrz] Adres zmiennej, która po powodzenie otrzymuje maksymalny czas w milisekundach, który pula wątków będzie czekać na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize

Wywołanie tej metody, aby ustawić liczbę wątków w puli.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parametry

*nNumThreads (Wyd.*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads jest ujemna,* jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków.

Jeśli *nNumThreads* wynosi zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w komputerze, aby uzyskać całkowitą liczbę wątków.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout

Wywołanie tej metody, aby ustawić maksymalny czas w milisekundach, że pula wątku będzie czekać na wątek do zamknięcia.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parametry

*dwMaxWait (Polski)*<br/>
Żądana maksymalna ilość czasu w milisekundach, że pula wątków będzie czekać na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)<br/>
[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)
