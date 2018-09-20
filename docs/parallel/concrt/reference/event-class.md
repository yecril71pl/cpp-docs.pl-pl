---
title: Event, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
dev_langs:
- C++
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e871255e3308450764e8f65cdb6acebe79df38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437745"
---
# <a name="event-class"></a>event — Klasa

Zdarzenie resetowania ręcznego, które jest jawnie świadome współbieżności środowiska wykonawczego.

## <a name="syntax"></a>Składnia

```
class event;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ event — destruktor](#dtor)|Niszczy zdarzenie.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Resetuj](#reset)|Resetuje zdarzenia do stanu zasygnalizowane.|
|[set](#set)|Sygnalizuje zdarzenie.|
|[Czekaj](#wait)|W tym czasie czeka na zdarzenie zostało zasygnalizowane.|
|[wait_for_multiple](#wait_for_multiple)|W tym czasie czeka na wiele zdarzeń zostało zasygnalizowane.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Wartość wskazująca, że oczekiwania nigdy nie powinny wygasać.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="ctor"></a> Zdarzenia

Tworzy nowe zdarzenie.

```
_CRTIMP event();
```

### <a name="remarks"></a>Uwagi

##  <a name="dtor"></a> ~ zdarzeń

Niszczy zdarzenie.

```
~event();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że nie istnieją wątki oczekujące na zdarzenie po uruchomieniu destruktora. Zezwalanie na zdarzenie niszczenia z wątkami, nadal oczekuje powoduje zachowanie niezdefiniowane.

##  <a name="reset"></a> Resetuj

Resetuje zdarzenia do stanu zasygnalizowane.

```
void reset();
```

##  <a name="set"></a> Zestaw

Sygnalizuje zdarzenie.

```
void set();
```

### <a name="remarks"></a>Uwagi

Sygnalizacja zdarzenie może spowodować dowolną liczbę kontekstów oczekujących aż zdarzenie stanie się możliwe do uruchomienia.

##  <a name="timeout_infinite"></a> timeout_infinite

Wartość wskazująca, że oczekiwania nigdy nie powinny wygasać.

```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

##  <a name="wait"></a> Czekaj

W tym czasie czeka na zdarzenie zostało zasygnalizowane.

```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_Limit czasu*<br/>
Wskazuje liczbę milisekund przed upływem limitu czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza brak limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli czas oczekiwania był zadawalający, wartość `0` jest zwracana; w przeciwnym razie wartość `COOPERATIVE_WAIT_TIMEOUT` do wskazania, że upłynął limit czasu oczekiwania bez zasygnalizowania zdarzenia.

> [!IMPORTANT]
>  W aplikacji platformy uniwersalnej Windows (UWP), nie należy wywoływać metody `wait` na wątku ASTA, ponieważ to wywołanie może zablokować bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać.

##  <a name="wait_for_multiple"></a> wait_for_multiple —

W tym czasie czeka na wiele zdarzeń zostało zasygnalizowane.

```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PPEvents*<br/>
Tablica zdarzeń oczekiwania. Liczba zdarzeń w tablicy jest wskazywana przez `count` parametru.

*Liczba*<br/>
Liczba zdarzeń w tablicy dostarczana w `_PPEvents` parametru.

*_FWaitAll*<br/>
Jeśli ustawiona na wartość `true`, parametr określa, że wszystkie zdarzenia w tablicy dostarczanej w `_PPEvents` parametru muszą być sygnalizowane, aby spełniać oczekiwanie. Jeśli ustawiona na wartość `false`, określa, że każde zdarzenie w tablicy dostarczanej w `_PPEvents` parametr, który jest sygnalizowany, będzie spełniać oczekiwania.

*_Limit czasu*<br/>
Wskazuje liczbę milisekund przed upływem limitu czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza brak limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli czas oczekiwania był zadawalający, indeks w tablicy dostarczany w `_PPEvents` parametr, który spełniającym warunek oczekiwania; w przeciwnym razie wartość `COOPERATIVE_WAIT_TIMEOUT` do wskazania, że upłynął limit czasu oczekiwania bez spełnienia warunku.

### <a name="remarks"></a>Uwagi

Jeśli parametr `_FWaitAll` jest ustawiona na wartość `true` wskazujący, że wszystkie zdarzenia muszą być sygnalizowane, aby zaspokoić oczekiwania, wskaźnik zwracany przez funkcję niesie ze sobą nie specjalnego znaczenie poza tym, że nie jest wartością `COOPERATIVE_WAIT_TIMEOUT`.

> [!IMPORTANT]
>  W aplikacji platformy uniwersalnej Windows (UWP), nie należy wywoływać metody `wait_for_multiple` na wątku ASTA, ponieważ to wywołanie może zablokować bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
