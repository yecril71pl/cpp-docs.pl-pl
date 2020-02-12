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
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138954"
---
# <a name="multitype_join-class"></a>multitype_join — Klasa

Blok komunikatów `multitype_join` to wieloźródłowy blok komunikatów z pojedynczym miejscem, który łączy połączenia różnych typów z poszczególnych źródeł i oferuje spójną kolekcję komunikatów z obiektami docelowymi.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
`tuple` typ ładunku komunikatów przyłączonych i rozpropagowanych przez blok.

*_Jtype*<br/>
Rodzaj bloku `join` to `greedy` lub `non_greedy`

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[multitype_join](#ctor)|Przeciążone. Tworzy blok komunikatów `multitype_join`.|
|[~ multitype_join destruktor](#dtor)|Niszczy blok komunikatów `multitype_join`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[odebrać](#accept)|Akceptuje komunikat, który został zaoferowany przez ten blok `multitype_join`, przez przeniesienie własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje liczbę odwołań w tym bloku komunikatów `multitype_join`, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `multitype_join` i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.|
|[link_target](#link_target)|Łączy blok docelowy z tym blokiem komunikatów `multitype_join`.|
|[Usuwanie](#release)|Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.|
|[release_ref](#release_ref)|Zwalnia liczbę odwołań w tym bloku komunikatów `multiple_join`.|
|[zarezerwować](#reserve)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `multitype_join`.|
|[unlink_target](#unlink_target)|Odłącza blok docelowy z tego bloku komunikatów `multitype_join`.|
|[unlink_targets](#unlink_targets)|Odłącza wszystkie elementy docelowe z tego bloku komunikatów `multitype_join`. (Przesłania [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a>odebrać

Akceptuje komunikat, który został zaoferowany przez ten blok `multitype_join`, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `accept`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

## <a name="acquire_ref"></a>acquire_ref

Uzyskuje liczbę odwołań w tym bloku komunikatów `multitype_join`, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest połączony z tym źródłem podczas `link_target` metody.

## <a name="consume"></a>wykorzystania

Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `multitype_join` i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zarezerwowanych obiektów `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `consume`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Metoda `consume` jest podobna do `accept`, ale zawsze musi być poprzedzona wywołaniem `reserve` zwracającym **wartość true**.

## <a name="link_target"></a>link_target

Łączy blok docelowy z tym blokiem komunikatów `multitype_join`.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku `ITarget`, aby połączyć ten blok komunikatów `multitype_join`.

## <a name="ctor"></a>multitype_join

Tworzy blok komunikatów `multitype_join`.

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
`tuple` źródeł dla tego bloku komunikatów `multitype_join`.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

*_Join*<br/>
Blok komunikatów `multitype_join` do skopiowania. Należy zauważyć, że oryginalny obiekt jest oddzielony, co czyni ten konstruktor przenoszenia.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Konstrukcja przenoszenia nie jest przeprowadzana w ramach blokady, co oznacza, że jest ona dostępna dla użytkownika, aby upewnić się, że w czasie przenoszenia nie ma żadnych lekkich zadań. W przeciwnym razie może wystąpić wiele Races, co prowadzi do wyjątków lub niespójnego stanu.

## <a name="dtor"></a>~ multitype_join

Niszczy blok komunikatów `multitype_join`.

```cpp
~multitype_join();
```

## <a name="release"></a>Usuwanie

Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `release`.

## <a name="release_ref"></a>release_ref

Zwalnia liczbę odwołań w tym bloku komunikatów `multiple_join`.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a>zarezerwować

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `multitype_join`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` obiektu `message`, który jest zarezerwowany.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `reserve`.

### <a name="return-value"></a>Wartość zwrócona

`true`, jeśli komunikat został pomyślnie zarezerwowany, `false` w przeciwnym razie. Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve`, jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu podjęcia lub zadawania wiadomości odpowiednio.

## <a name="unlink_target"></a>unlink_target

Odłącza blok docelowy z tego bloku komunikatów `multitype_join`.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku `ITarget`, aby odłączyć od tego bloku komunikatów `multitype_join`.

## <a name="unlink_targets"></a>unlink_targets

Odłącza wszystkie elementy docelowe z tego bloku komunikatów `multitype_join`.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[choice, klasa](choice-class.md)<br/>
[join, klasa](join-class.md)
