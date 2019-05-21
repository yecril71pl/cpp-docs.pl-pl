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
ms.openlocfilehash: 89e6d972fbecb2674e6343bf6d11f9972c25c63d
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975035"
---
# <a name="tilebarrier-class"></a>tile_barrier — Klasa

Synchronizuje wykonywanie wątków uruchomionych w grupie wątku (fragment) za pomocą `wait` metod. Tylko środowisko uruchomieniowe może utworzyć wystąpienie tej klasy.

### <a name="syntax"></a>Składnia

```
class tile_barrier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[tile_barrier Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `tile_barrier` klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czekaj](#wait)|Powoduje, że wszystkie wątki w grupie wątku (fragment), aby zatrzymać wykonywanie, dopóki wszystkie wątki we fragmencie zakończą oczekiwanie.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich dostępów do pamięci oraz gdy wszystkie wątki we fragmencie osiągną to wywołanie.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie do momentu zakończenia wszystkich dostępów do pamięci globalnej oraz wszystkie wątki we fragmencie osiągną to wywołanie.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje wykonanie wszystkich wątków we fragmencie, aż wszystkie `tile_static` dostępy do pamięci oraz gdy wszystkie wątki we fragmencie osiągną to wywołanie.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tile_barrier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amp.h

**Namespace:** Współbieżność

## <a name="ctor"></a>  tile_barrier — Konstruktor

Inicjuje nowe wystąpienie klasy przez skopiowanie istniejącego.

### <a name="syntax"></a>Składnia

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`tile_barrier` Obiektu do skopiowania.

## <a name="wait"></a>Czekaj

Powoduje, że wszystkie wątki w grupie wątku (fragment), aby zatrzymać wykonywanie, dopóki wszystkie wątki we fragmencie zakończą oczekiwanie.

### <a name="syntax"></a>Składnia

```
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a> wait_with_all_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie do momentu wszystkie wątki we fragmencie osiągną to wywołanie. Zapewnia to, że wszystkie dostępy do pamięci są widoczne dla innych wątków w pliku wątku i zostały wykonane w porządku program.

### <a name="syntax"></a>Składnia

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewaitwithglobalmemoryfence-waitwithglobalmemoryfence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie do momentu wszystkie wątki we fragmencie osiągną to wywołanie. Zapewnia to, że wszystkie dostępy do pamięci globalnej są widoczne dla innych wątków w pliku wątku i zostały wykonane w porządku program.

### <a name="syntax"></a>Składnia

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewaitwithtilestaticmemoryfence-waitwithtilestaticmemoryfence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence —

Blokuje wykonanie wszystkich wątków we fragmencie do momentu wszystkie wątki we fragmencie osiągną to wywołanie. Gwarantuje to, że `tile_static` pamięci uzyskuje dostęp do są widoczne dla innych wątków w pliku wątku i zostały wykonane w porządku program.

### <a name="syntax"></a>Składnia

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
