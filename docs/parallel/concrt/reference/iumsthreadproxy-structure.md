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
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139963"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy — Struktura

Abstrakcja wątku wykonania. Jeśli chcesz, aby harmonogram przyznał wątki harmonogramie (UMS), ustaw wartość dla elementu zasad harmonogramu `SchedulerKind` na `UmsThreadDefault`i zaimplementuj interfejs `IUMSScheduler`. Wątki UMS są obsługiwane tylko w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IUMSThreadProxy:: EnterCriticalRegion —](#entercriticalregion)|Wywoływana w celu wprowadzenia regionu krytycznego. W ramach regionu krytycznego harmonogram nie będzie obserwować asynchronicznych operacji blokowania, które są wykonywane w danym regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony dla błędów strony, zawieszeń wątku, asynchronicznych wywołań procedur jądra (APCs) i tak dalej, dla wątku UMS.|
|[IUMSThreadProxy:: EnterHyperCriticalRegion —](#enterhypercriticalregion)|Wywoływana w celu wprowadzenia regionu krytycznego dla funkcji Hyper-in. W regionie o krytycznym znaczeniu dla funkcji harmonogram nie będzie obserwować żadnych operacji blokowania, które są wykonywane w danym regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony w celu zablokowania wywołań funkcji, blokady zawieszania, które blokują, błędy stron, zawieszenia wątku, asynchroniczne wywołania procedur jądra (APCs) i tak dalej, dla wątku UMS.|
|[IUMSThreadProxy:: ExitCriticalRegion —](#exitcriticalregion)|Wywoływana w celu opuszczenia regionu krytycznego.|
|[IUMSThreadProxy:: ExitHyperCriticalRegion —](#exithypercriticalregion)|Wywołuje się, by wyjść z regionu krytycznego dla funkcji Hyper-krytyczny.|
|[IUMSThreadProxy:: GetCriticalRegionType —](#getcriticalregiontype)|Zwraca rodzaj regionu krytycznego, w którym znajduje się serwer proxy wątku. Ze względu na to, że regiony krytyczne dla funkcji Hyper są nadzbiorem regionów krytycznych, w przypadku wprowadzenia kodu do regionu krytycznego, a następnie regionu krytycznego dla funkcji Hyper `InsideHyperCriticalRegion` zostaną zwrócone.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="entercriticalregion"></a>IUMSThreadProxy:: EnterCriticalRegion —, Metoda

Wywoływana w celu wprowadzenia regionu krytycznego. W ramach regionu krytycznego harmonogram nie będzie obserwować asynchronicznych operacji blokowania, które są wykonywane w danym regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony dla błędów strony, zawieszeń wątku, asynchronicznych wywołań procedur jądra (APCs) i tak dalej, dla wątku UMS.

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowa głębokość regionu krytycznego. Obszary krytyczne są współużytkowane.

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy:: EnterHyperCriticalRegion —, Metoda

Wywoływana w celu wprowadzenia regionu krytycznego dla funkcji Hyper-in. W regionie o krytycznym znaczeniu dla funkcji harmonogram nie będzie obserwować żadnych operacji blokowania, które są wykonywane w danym regionie. Oznacza to, że harmonogram nie zostanie ponownie wprowadzony w celu zablokowania wywołań funkcji, blokady zawieszania, które blokują, błędy stron, zawieszenia wątku, asynchroniczne wywołania procedur jądra (APCs) i tak dalej, dla wątku UMS.

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowa głębokość regionu krytycznego dla funkcji Hyper-lokacja. Regiony krytyczne dla funkcji Hyper są współużytkowane.

### <a name="remarks"></a>Uwagi

Harmonogram musi być bardzo ostrożnie na temat metod wywoływanych przez nią i blokad, które są w tych regionach. Jeśli kod w tym regionie blokuje blokadę, która jest utrzymywana przez coś, że harmonogram jest odpowiedzialny za planowanie, zakleszczenie może nastąpić.

## <a name="exitcriticalregion"></a>IUMSThreadProxy:: ExitCriticalRegion —, Metoda

Wywoływana w celu opuszczenia regionu krytycznego.

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowa głębokość regionu krytycznego. Obszary krytyczne są współużytkowane.

## <a name="exithypercriticalregion"></a>IUMSThreadProxy:: ExitHyperCriticalRegion —, Metoda

Wywołuje się, by wyjść z regionu krytycznego dla funkcji Hyper-krytyczny.

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Nowa głębokość regionu krytycznego dla funkcji Hyper-lokacja. Regiony krytyczne dla funkcji Hyper są współużytkowane.

## <a name="getcriticalregiontype"></a>IUMSThreadProxy:: GetCriticalRegionType —, Metoda

Zwraca rodzaj regionu krytycznego, w którym znajduje się serwer proxy wątku. Ze względu na to, że regiony krytyczne dla funkcji Hyper są nadzbiorem regionów krytycznych, w przypadku wprowadzenia kodu do regionu krytycznego, a następnie regionu krytycznego dla funkcji Hyper `InsideHyperCriticalRegion` zostaną zwrócone.

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Typ regionu krytycznego, w którym znajduje się serwer proxy wątku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)
