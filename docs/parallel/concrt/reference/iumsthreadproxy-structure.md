---
title: IUMSThreadProxy — Struktura
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368081"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy — Struktura

Abstrakcja dla wątku wykonania. Jeśli chcesz, aby harmonogram był przyznawany wątkom w trybie ums (UMS), `SchedulerKind` ustaw `UmsThreadDefault`wartość elementu `IUMSScheduler` zasad harmonogramu na , i zaimplementuj interfejs. Wątki usługi UMS są obsługiwane tylko w 64-bitowych systemach operacyjnych w wersji Windows 7 lub nowszej.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Wywoływana w celu wejścia w krytyczny region. W regionie krytycznym harmonogram nie będzie obserwować asynchronicznych operacji blokowania, które mają miejsce w regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony dla błędów strony, zawieszenia wątku, wywołania procedury asynchroniczne jądra (APC) i tak dalej dla wątku UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Wywoływana w celu wprowadzenia regionu hiperkrytycznym. W regionie hiperkrytycznym harmonogram nie będzie obserwować żadnych operacji blokowania, które mają miejsce w regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony do blokowania wywołań funkcji, blokowania prób nabycia, które blokują, błędy strony, zawieszenia wątku, wywołania procedur asynchronicznych jądra (APC) i tak dalej, dla wątku UMS.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Wywoływane w celu wyjścia z krytycznego regionu.|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|Wywoływane w celu wyjścia z regionu hiperkrytycznym.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Zwraca rodzaj regionu krytycznego serwera proxy wątku. Ponieważ regiony o znaczeniu hiperkrytycznym są nadzbiorem regionów krytycznych, jeśli kod `InsideHyperCriticalRegion` wszedł w region krytyczny, a następnie region hiperkrytyczny, zostanie zwrócony.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThreadProxy::Metoda EnterCriticalRegion

Wywoływana w celu wejścia w krytyczny region. W regionie krytycznym harmonogram nie będzie obserwować asynchronicznych operacji blokowania, które mają miejsce w regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony dla błędów strony, zawieszenia wątku, wywołania procedury asynchroniczne jądra (APC) i tak dalej dla wątku UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Nowa głębokość krytycznego regionu. Regiony krytyczne są reentrant.

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThreadProxy::Metoda EnterHyperCriticalRegion

Wywoływana w celu wprowadzenia regionu hiperkrytycznym. W regionie hiperkrytycznym harmonogram nie będzie obserwować żadnych operacji blokowania, które mają miejsce w regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony do blokowania wywołań funkcji, blokowania prób nabycia, które blokują, błędy strony, zawieszenia wątku, wywołania procedur asynchronicznych jądra (APC) i tak dalej, dla wątku UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Nowa głębokość regionu hiperkrytycznym. Regiony o znaczeniu krytycznym są reentrant.

### <a name="remarks"></a>Uwagi

Harmonogram musi być niezwykle ostrożny, jakie metody wywołuje i jakie blokady nabywa w takich regionach. Jeśli kod w takim regionie blokuje na blokadzie, która jest utrzymywana przez coś, co harmonogram jest odpowiedzialny za planowanie, może wystąpić zakleszczenie.

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThreadProxy::ExitCriticalRegion Metoda

Wywoływane w celu wyjścia z krytycznego regionu.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Nowa głębokość krytycznego regionu. Regiony krytyczne są reentrant.

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThreadProxy::ExitHyperCriticalRegion Metoda

Wywoływane w celu wyjścia z regionu hiperkrytycznym.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Nowa głębokość regionu hiperkrytycznym. Regiony o znaczeniu krytycznym są reentrant.

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThreadProxy::Metoda GetCriticalRegionType

Zwraca rodzaj regionu krytycznego serwera proxy wątku. Ponieważ regiony o znaczeniu hiperkrytycznym są nadzbiorem regionów krytycznych, jeśli kod `InsideHyperCriticalRegion` wszedł w region krytyczny, a następnie region hiperkrytyczny, zostanie zwrócony.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Typ regionu krytycznego serwera proxy wątku znajduje się w obrębie.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)
