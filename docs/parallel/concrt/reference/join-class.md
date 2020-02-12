---
title: join — Klasa
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139851"
---
# <a name="join-class"></a>join — Klasa

Blok komunikatów `join` to Jednoelementowy, uporządkowany `propagator_block`, który łączy razem komunikaty typu `T` z każdego ze źródeł.

## <a name="syntax"></a>Składnia

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku komunikatów przyłączonych i rozpropagowanych przez blok.

*_Jtype*<br/>
Rodzaj bloku `join` to `greedy` lub `non_greedy`

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[join](#ctor)|Przeciążone. Tworzy blok komunikatów `join`.|
|[~ Join — destruktor](#dtor)|Niszczy blok `join`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `join`, przekazując własność do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `join` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `join`.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `join`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Konstruuje komunikat wyjściowy zawierający komunikat wejściowy z każdego źródła, gdy ma on propagowany komunikat. Wysyła ten komunikat wyjściowy do każdego z jego obiektów docelowych.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `join`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `join`, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `join` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zużywanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale jest zawsze poprzedzone wywołaniem `reserve`.

## <a name="ctor"></a>Złącza

Tworzy blok komunikatów `join`.

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_NumInputs*<br/>
Liczba danych wejściowych tego bloku `join` będzie dozwolona.

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `join`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `join`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `filter_method` to Funktor z sygnaturą `bool (T const &)`, która jest wywoływana przez ten blok komunikatów `join` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="dtor"></a>~ Join

Niszczy blok `join`.

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `join`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `join`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Konstruuje komunikat wyjściowy zawierający komunikat wejściowy z każdego źródła, gdy ma on propagowany komunikat. Wysyła ten komunikat wyjściowy do każdego z jego obiektów docelowych.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

## <a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

## <a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `join`.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli komunikat został pomyślnie zarezerwowany, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve`, jeśli zwraca **wartość true**, należy wywołać `consume` lub `release`, aby przejąć lub zwolnić własność wiadomości.

## <a name="resume_propagation"></a>resume_propagation

Wznawia propagację po wydaniu rezerwacji.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[choice, klasa](choice-class.md)<br/>
[multitype_join, klasa](multitype-join-class.md)
