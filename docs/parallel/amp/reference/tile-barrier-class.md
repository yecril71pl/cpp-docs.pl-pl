---
title: tile_barrier — Klasa
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: c00f1e41e70e723be185959eeff176390def7647
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374723"
---
# <a name="tile_barrier-class"></a>tile_barrier — Klasa

Synchronizuje wykonywanie wątków, które są uruchomione w grupie wątków `wait` (kafelka) przy użyciu metod. Tylko środowisko wykonawcze można utworzyć wystąpienia tej klasy.

## <a name="syntax"></a>Składnia

```cpp
class tile_barrier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor tile_barrier](#ctor)|Inicjuje nowe wystąpienie klasy `tile_barrier`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czekać](#wait)|Nakazuje wszystkie wątki w grupie wątków (kafelka), aby zatrzymać wykonywanie, dopóki wszystkie wątki w kafelku nie zakończą oczekiwania.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blokuje wykonywanie wszystkich wątków w kafelku, dopóki nie zostaną ukończone wszystkie dostępy do pamięci i wszystkie wątki w kafelku osiągnęły to wywołanie.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blokuje wykonywanie wszystkich wątków w kafelku, dopóki nie zostaną ukończone wszystkie dostępy do pamięci globalnej i wszystkie wątki na kafelku osiągnęły to wywołanie.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje wykonywanie wszystkich wątków w kafelku, dopóki nie zostaną ukończone wszystkie `tile_static` dostępy do pamięci i wszystkie wątki w kafelku osiągnęły to wywołanie.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tile_barrier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Obszar nazw:** Współbieżności

## <a name="tile_barrier-constructor"></a><a name="ctor"></a>Konstruktor tile_barrier

Inicjuje nowe wystąpienie klasy, kopiując istniejące.

### <a name="syntax"></a>Składnia

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `tile_barrier` do skopiowania.

## <a name="wait"></a>czas oczekiwania

Nakazuje wszystkie wątki w grupie wątków (kafelka), aby zatrzymać wykonywanie, dopóki wszystkie wątki w kafelku nie zakończą oczekiwania.

### <a name="syntax"></a>Składnia

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku, dopóki wszystkie wątki w kafelku nie osiągną tego wywołania. Gwarantuje to, że wszystkie dostępy do pamięci są widoczne dla innych wątków na kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence">wait_with_global_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku, dopóki wszystkie wątki w kafelku nie osiągną tego wywołania. Gwarantuje to, że wszystkie dostępy do pamięci globalnej są widoczne dla innych wątków na kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence">wait_with_tile_static_memory_fence

Blokuje wykonywanie wszystkich wątków w kafelku, dopóki wszystkie wątki w kafelku nie osiągną tego wywołania. Gwarantuje to, `tile_static` że dostęp do pamięci są widoczne dla innych wątków na kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Zobacz też

[Obszar nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
