---
title: event — Klasa
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 3f2ec71083f7a7905bad5cda014baba914e31e79
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215806"
---
# <a name="event-class"></a>event — Klasa

Zdarzenie resetowania ręcznego, które jest jawnie świadome środowisko uruchomieniowe współbieżności.

## <a name="syntax"></a>Składnia

```cpp
class event;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ — Destruktor zdarzenia](#dtor)|Niszczy zdarzenie.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[zresetować](#reset)|Resetuje zdarzenie do stanu niesygnalizowanego.|
|[zbiór](#set)|Sygnalizuje zdarzenie.|
|[trwa](#wait)|Czeka, aż zdarzenie zostanie zasygnalizowane.|
|[wait_for_multiple](#wait_for_multiple)|Czeka na zasygnalizowanie wielu zdarzeń.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Wartość wskazująca, że oczekiwania nigdy nie powinien przekraczać limitu czasu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

**Przestrzeń nazw:** współbieżność

## <a name="event"></a><a name="ctor"></a>wydarzen

Tworzy nowe zdarzenie.

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>Uwagi

## <a name="event"></a><a name="dtor"></a>~ zdarzenie

Niszczy zdarzenie.

```cpp
~event();
```

### <a name="remarks"></a>Uwagi

Oczekuje się, że nie ma wątków oczekujących na zdarzenie, gdy destruktor jest uruchomiony. Umożliwienie zdarzeniu destruktora z wątkami nadal czeka na to zachowanie niezdefiniowane.

## <a name="reset"></a><a name="reset"></a>zresetować

Resetuje zdarzenie do stanu niesygnalizowanego.

```cpp
void reset();
```

## <a name="set"></a><a name="set"></a>zbiór

Sygnalizuje zdarzenie.

```cpp
void set();
```

### <a name="remarks"></a>Uwagi

Sygnalizowanie zdarzenia może spowodować dowolną liczbę kontekstów oczekujących na zdarzenie, aby stał się możliwy do uruchomienia.

## <a name="timeout_infinite"></a><a name="timeout_infinite"></a>timeout_infinite

Wartość wskazująca, że oczekiwania nigdy nie powinien przekraczać limitu czasu.

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a><a name="wait"></a>trwa

Czeka, aż zdarzenie zostanie zasygnalizowane.

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Wskazuje liczbę milisekund przed upływem limitu czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza, że nie ma limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli oczekiwanie zakończyło się, wartość `0` jest zwracana; w przeciwnym razie wartość, `COOPERATIVE_WAIT_TIMEOUT` Aby wskazać, że upłynął limit czasu oczekiwania bez zasygnalizowania zdarzenia.

> [!IMPORTANT]
> W aplikacji platforma uniwersalna systemu Windows (platformy UWP) Nie wywołuj do `wait` wątku ASTA, ponieważ to wywołanie może blokować bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać.

## <a name="wait_for_multiple"></a><a name="wait_for_multiple"></a>wait_for_multiple

Czeka na zasygnalizowanie wielu zdarzeń.

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PPEvents*<br/>
Tablica zdarzeń do zaczekania. Liczba zdarzeń w tablicy jest wskazywana przez `count` parametr.

*liczbą*<br/>
Liczba zdarzeń w tablicy dostarczonej w `_PPEvents` parametrze.

*_FWaitAll*<br/>
Jeśli ustawiona na wartość **`true`** , parametr określa, że wszystkie zdarzenia w tablicy dostarczonej w `_PPEvents` parametrze muszą zostać zasygnalizowanie w celu zaspokojenia oczekiwania. Jeśli zostanie ustawiona na wartość **`false`** , określa, że każde zdarzenie w tablicy dostarczonej w `_PPEvents` parametrze, który zostanie zasygnalizowanie, będzie spełniać oczekiwania.

*_Timeout*<br/>
Wskazuje liczbę milisekund przed upływem limitu czasu oczekiwania. Wartość `COOPERATIVE_TIMEOUT_INFINITE` oznacza, że nie ma limitu czasu.

### <a name="return-value"></a>Wartość zwracana

Jeśli oczekiwanie zakończyło się, indeks w tablicy dostarczanej w `_PPEvents` parametrze, który spełnia warunek oczekiwania; w przeciwnym razie wartość, `COOPERATIVE_WAIT_TIMEOUT` Aby wskazać, że upłynął limit czasu oczekiwania bez spełnienia warunku.

### <a name="remarks"></a>Uwagi

Jeśli parametr `_FWaitAll` jest ustawiony na wartość, **`true`** Aby wskazać, że wszystkie zdarzenia muszą być sygnalizowane do zaspokojenia oczekiwania, indeks zwrócony przez funkcję nie niesie ze sobą specjalnego znaczenia poza faktem, że nie jest wartością `COOPERATIVE_WAIT_TIMEOUT` .

> [!IMPORTANT]
> W aplikacji platforma uniwersalna systemu Windows (platformy UWP) Nie wywołuj do `wait_for_multiple` wątku ASTA, ponieważ to wywołanie może blokować bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
