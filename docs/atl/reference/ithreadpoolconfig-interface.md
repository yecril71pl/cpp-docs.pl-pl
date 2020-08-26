---
title: IThreadPoolConfig, interfejs
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
ms.openlocfilehash: cba82055c292fc966dc2328773cce4aa64d45a64
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835431"
---
# <a name="ithreadpoolconfig-interface"></a>IThreadPoolConfig, interfejs

Ten interfejs zapewnia metody konfigurowania puli wątków.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.|
|[GetTimeout](#gettimeout)|Wywołaj tę metodę, aby uzyskać maksymalny czas w milisekundach, przez który Pula wątków będzie czekać na zamknięcie wątku.|
|[SetSize](#setsize)|Wywołaj tę metodę, aby ustawić liczbę wątków w puli.|
|[SetTimeout](#settimeout)|Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.|

## <a name="remarks"></a>Uwagi

Ten interfejs jest implementowany przez [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlutil. h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a> IThreadPoolConfig:: GetSize

Wywołaj tę metodę, aby uzyskać liczbę wątków w puli.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
określoną Adres zmiennej, która po powodzeniu odbiera liczbę wątków w puli.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a> IThreadPoolConfig:: GetTimeout

Wywołaj tę metodę, aby uzyskać maksymalny czas w milisekundach, przez który Pula wątków będzie czekać na zamknięcie wątku.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
określoną Adres zmiennej, która po sukcesie odbiera maksymalny czas w milisekundach, przez który Pula wątków czeka na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig:: GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a> IThreadPoolConfig:: setSize

Wywołaj tę metodę, aby ustawić liczbę wątków w puli.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Żądana liczba wątków w puli.

Jeśli *nNumThreads* jest ujemna, jego wartość bezwzględna zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków.

Jeśli *nNumThreads* ma wartość zero, ATLS_DEFAULT_THREADSPERPROC zostanie pomnożona przez liczbę procesorów w maszynie, aby uzyskać łączną liczbę wątków.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig:: GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a> IThreadPoolConfig:: setTimeout

Wywołaj tę metodę, aby ustawić maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Żądany maksymalny czas (w milisekundach) oczekiwania puli wątków na zamknięcie wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="example"></a>Przykład

Zobacz [IThreadPoolConfig:: GetSize](#getsize).

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)<br/>
[Klasa CThreadPool](../../atl/reference/cthreadpool-class.md)
