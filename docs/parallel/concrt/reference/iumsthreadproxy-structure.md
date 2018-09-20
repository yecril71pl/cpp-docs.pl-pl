---
title: Iumsthreadproxy — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 573bee042788f03278abc78fbc541c933d693907
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417387"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy — Struktura

Abstrakcja wątku wykonywania. Harmonogramu uzyskają wątków (UMS) ustalonych w harmonogramie trybu użytkownika, należy ustawić wartość dla elementu zasad harmonogramu `SchedulerKind` do `UmsThreadDefault`i zaimplementować `IUMSScheduler` interfejsu. UMS wątki są tylko obsługiwane w systemie 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.

## <a name="syntax"></a>Składnia

```
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|Wywołuje się, aby krytyczne regionu. Gdy wewnątrz regionu krytycznych, harmonogram nie obowiązują blokowania operacji asynchronicznych, które odbywa się w regionie. Oznacza to, że harmonogram zostanie nie trzeba ponownie wprowadzić błędów stron, zawieszenia wątku, wywołań asynchronicznych procedur jądra (APCs) i tak dalej dla wątku UMS.|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|Wywołuje się, aby hyper krytyczne regionu. Gdy wewnątrz funkcji hyper krytyczny regionu, harmonogram nie obowiązują blokowania operacji, które zdarzają się w regionie. Oznacza to, że nie będzie trzeba ponownie wprowadzić harmonogram dotyczące blokowania wywołań funkcji, prób przejęcia blokady z bloków, stron błędów, wątek zawieszenia wywołań asynchronicznych procedur jądra (APCs) i innych elementów, aby uzyskać UMS wątku.|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|Wywołuje się, aby można było zakończyć krytyczne regionu.|
|[Iumsthreadproxy::exithypercriticalregion —](#exithypercriticalregion)|Wywołuje się, aby zakończyć działanie funkcji hyper krytyczny regionu.|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|Zwraca rodzaj krytyczne region proxy wątku znajduje się w. Ponieważ hyper krytyczne regiony są podzbiorem krytyczne regionów, jeśli wprowadzony kod krytyczne regionu, a następnie obszarem hyper krytyczne `InsideHyperCriticalRegion` zostaną zwrócone.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="entercriticalregion"></a>  Iumsthreadproxy::entercriticalregion — metoda

Wywołuje się, aby krytyczne regionu. Gdy wewnątrz regionu krytycznych, harmonogram nie obowiązują blokowania operacji asynchronicznych, które odbywa się w regionie. Oznacza to, że harmonogram zostanie nie trzeba ponownie wprowadzić błędów stron, zawieszenia wątku, wywołań asynchronicznych procedur jądra (APCs) i tak dalej dla wątku UMS.

```
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość nowy region krytycznych. Krytyczne regiony są współużytkowane.

##  <a name="enterhypercriticalregion"></a>  Iumsthreadproxy::enterhypercriticalregion — metoda

Wywołuje się, aby hyper krytyczne regionu. Gdy wewnątrz funkcji hyper krytyczny regionu, harmonogram nie obowiązują blokowania operacji, które zdarzają się w regionie. Oznacza to, że nie będzie trzeba ponownie wprowadzić harmonogram dotyczące blokowania wywołań funkcji, prób przejęcia blokady z bloków, stron błędów, wątek zawieszenia wywołań asynchronicznych procedur jądra (APCs) i innych elementów, aby uzyskać UMS wątku.

```
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość nowych funkcji hyper krytyczny regionu. Funkcji Hyper krytyczny regiony są współużytkowane.

### <a name="remarks"></a>Uwagi

Harmonogram należy ostrożnie bardzo metod wywoływanych przez nią i co umożliwia zablokowanie uzyskuje w tych regionach. Jeśli kod w tych regionów blokuje na blokadę, będącego w posiadaniu coś, co jest odpowiedzialna za planowanie harmonogramu, może pojawić się zakleszczenia.

##  <a name="exitcriticalregion"></a>  Iumsthreadproxy::exitcriticalregion — metoda

Wywołuje się, aby można było zakończyć krytyczne regionu.

```
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość nowy region krytycznych. Krytyczne regiony są współużytkowane.

##  <a name="exithypercriticalregion"></a>  Iumsthreadproxy::exithypercriticalregion — metoda

Wywołuje się, aby zakończyć działanie funkcji hyper krytyczny regionu.

```
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość nowych funkcji hyper krytyczny regionu. Funkcji Hyper krytyczny regiony są współużytkowane.

##  <a name="getcriticalregiontype"></a>  Iumsthreadproxy::getcriticalregiontype — metoda

Zwraca rodzaj krytyczne region proxy wątku znajduje się w. Ponieważ hyper krytyczne regiony są podzbiorem krytyczne regionów, jeśli wprowadzony kod krytyczne regionu, a następnie obszarem hyper krytyczne `InsideHyperCriticalRegion` zostaną zwrócone.

```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Typ krytyczne regionu, który mieści się wątek serwera proxy.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[IUMSScheduler, struktura](iumsscheduler-structure.md)
