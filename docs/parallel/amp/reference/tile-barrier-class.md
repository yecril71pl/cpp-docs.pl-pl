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
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855923"
---
# <a name="tile_barrier-class"></a>tile_barrier — Klasa

Synchronizuje wykonywanie wątków, które są uruchomione w grupie wątków (kafelek) przy użyciu metod `wait`. Tylko środowisko uruchomieniowe może utworzyć wystąpienie tej klasy.

## <a name="syntax"></a>Składnia

```cpp
class tile_barrier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor tile_barrier](#ctor)|Inicjuje nowe wystąpienie klasy `tile_barrier`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[trwa](#wait)|Instruuje wszystkie wątki w grupie wątków (kafelek), aby zatrzymać wykonywanie do momentu zakończenia wszystkich wątków na kafelku.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich operacji dostępu do pamięci, a wszystkie wątki we fragmencie osiągną to wywołanie.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich operacji dostępu do pamięci globalnej, a wszystkie wątki we fragmencie osiągną to wywołanie.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje wykonywanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich `tile_static` dostępu do pamięci, a wszystkie wątki we fragmencie osiągną to wywołanie.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tile_barrier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp. h

**Przestrzeń nazw:** Współbieżności

## <a name="ctor"></a>Konstruktor tile_barrier

Inicjuje nowe wystąpienie klasy przez skopiowanie istniejącej.

### <a name="syntax"></a>Składnia

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `tile_barrier` do skopiowania.

## <a name="wait"></a>trwa

Instruuje wszystkie wątki w grupie wątków (kafelek), aby zatrzymać wykonywanie do momentu zakończenia wszystkich wątków na kafelku.

### <a name="syntax"></a>Składnia

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Blokuje wykonywanie wszystkich wątków we fragmencie, dopóki wszystkie wątki we fragmencie osiągną to wywołanie. Daje to pewność, że wszystkie dostępy do pamięci są widoczne dla innych wątków w kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

Blokuje wykonywanie wszystkich wątków we fragmencie, dopóki wszystkie wątki we fragmencie osiągną to wywołanie. Gwarantuje to, że wszystkie dostępy do pamięci globalnej są widoczne dla innych wątków w kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

Blokuje wykonywanie wszystkich wątków we fragmencie, dopóki wszystkie wątki we fragmencie osiągną to wywołanie. Zapewnia to, że `tile_static` dostępy do pamięci są widoczne dla innych wątków w kafelku wątku i zostały wykonane w kolejności programu.

### <a name="syntax"></a>Składnia

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
