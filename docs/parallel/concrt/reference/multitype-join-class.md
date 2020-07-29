---
title: multitype_join — Klasa
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: c648e77e404cf39eab281a93e03d8b427da375f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205863"
---
# <a name="multitype_join-class"></a>multitype_join — Klasa

`multitype_join`Blok komunikatów to wieloźródłowy blok komunikatów z jednym elementem docelowym, który łączy połączenia różnych typów z poszczególnych źródeł i oferuje spójną kolekcję komunikatów z obiektami docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
`tuple`Typ ładunku komunikatów przyłączonych i rozpropagowanych przez blok.

*_Jtype*<br/>
Rodzaj `join` bloku to, `greedy` albo`non_greedy`

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T` .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[multitype_join](#ctor)|Przeciążone. Tworzy `multitype_join` blok komunikatów.|
|[~ multitype_join destruktor](#dtor)|Niszczy `multitype_join` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[odebrać](#accept)|Akceptuje komunikat, który był oferowany przez ten `multitype_join` blok, przekazując własność do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje liczbę odwołań w tym `multitype_join` bloku komunikatów, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Wykorzystuje komunikat wcześniej oferowany przez `multitype_join` blok komunikatów i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.|
|[link_target](#link_target)|Łączy blok docelowy z tym `multitype_join` blokiem obsługi komunikatów.|
|[Usuwanie](#release)|Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.|
|[release_ref](#release_ref)|Zwalnia liczbę odwołań w tym `multiple_join` bloku komunikatów.|
|[zarezerwować](#reserve)|Rezerwuje komunikat wcześniej oferowany przez ten `multitype_join` blok komunikatów.|
|[unlink_target](#unlink_target)|Odłącza blok docelowy z tego `multitype_join` bloku komunikatów.|
|[unlink_targets](#unlink_targets)|Odłącza wszystkie elementy docelowe z tego `multitype_join` bloku komunikatów. (Przesłania [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a><a name="accept"></a>odebrać

Akceptuje komunikat, który był oferowany przez ten `multitype_join` blok, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `accept` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

Uzyskuje liczbę odwołań w tym `multitype_join` bloku komunikatów, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączony z tym źródłem podczas tej `link_target` metody.

## <a name="consume"></a><a name="consume"></a>wykorzystania

Wykorzystuje komunikat wcześniej oferowany przez `multitype_join` blok komunikatów i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity`Obiekt zastrzeżony `message` .

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `consume` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

`consume`Metoda jest podobna do `accept` , ale musi być zawsze poprzedzona wywołaniem `reserve` zwracanym **`true`** .

## <a name="link_target"></a><a name="link_target"></a>link_target

Łączy blok docelowy z tym `multitype_join` blokiem obsługi komunikatów.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku do łączenia z tym `multitype_join` blokiem obsługi komunikatów.

## <a name="multitype_join"></a><a name="ctor"></a>multitype_join

Tworzy `multitype_join` blok komunikatów.

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>Parametry

*_Tuple*<br/>
`tuple`Źródło dla tego `multitype_join` bloku obsługi komunikatów.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `multitype_join` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `multitype_join` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

*_Join*<br/>
`multitype_join`Blok komunikatów do skopiowania. Należy zauważyć, że oryginalny obiekt jest oddzielony, co czyni ten konstruktor przenoszenia.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Konstrukcja przenoszenia nie jest przeprowadzana w ramach blokady, co oznacza, że jest ona dostępna dla użytkownika, aby upewnić się, że w czasie przenoszenia nie ma żadnych lekkich zadań. W przeciwnym razie może wystąpić wiele Races, co prowadzi do wyjątków lub niespójnego stanu.

## <a name="multitype_join"></a><a name="dtor"></a>~ multitype_join

Niszczy `multitype_join` blok komunikatów.

```cpp
~multitype_join();
```

## <a name="release"></a><a name="release"></a>Usuwanie

Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `release` metodę.

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

Zwalnia liczbę odwołań w tym `multiple_join` bloku komunikatów.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a><a name="reserve"></a>zarezerwować

Rezerwuje komunikat wcześniej oferowany przez ten `multitype_join` blok komunikatów.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Obiekt, który jest `runtime_object_identity` `message` zarezerwowany.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `reserve` metodę.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie. Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve` , jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu przeprowadzenia lub zadawać swój komunikat odpowiednio.

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

Odłącza blok docelowy z tego `multitype_join` bloku komunikatów.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku do odłączenia od tego `multitype_join` bloku komunikatów.

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

Odłącza wszystkie elementy docelowe z tego `multitype_join` bloku komunikatów.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Choice — Klasa](choice-class.md)<br/>
[join — Klasa](join-class.md)
