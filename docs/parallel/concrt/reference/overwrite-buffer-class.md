---
title: Klasa overwrite_buffer
ms.date: 11/04/2016
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 5b222170112f43ae9700054f42e1368545612d00
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138800"
---
# <a name="overwrite_buffer-class"></a>Klasa overwrite_buffer

Blok komunikatów `overwrite_buffer` to wiele obiektów, które mają uporządkowane `propagator_block` z możliwością jednoczesnego przechowywania pojedynczej wiadomości. Nowe wiadomości zastępują wcześniej przechowywane.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku komunikatów przechowywanych i propagowanych przez bufor.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Przeciążone. Tworzy blok komunikatów `overwrite_buffer`.|
|[~ overwrite_buffer destruktor](#dtor)|Niszczy blok komunikatów `overwrite_buffer`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy ten blok `overwrite_buffer` Messaging ma jeszcze wartość.|
|[value](#value)|Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w bloku komunikatów `overwrite_buffer`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `overwrite_buffer`, zwracając kopię komunikatu do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `overwrite_buffer` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `overwrite_buffer`.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `overwrite_buffer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym bloku komunikatów `overwrite_buffer` i oferuje go wszystkim połączonym obiektom docelowym.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `overwrite_buffer`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `overwrite_buffer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Blok `overwrite_buffer` Messaging propaguje kopie przechowywanych komunikatów do każdego z jego obiektów docelowych.

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `overwrite_buffer`, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Blok komunikatów `overwrite_buffer` zwraca kopie wiadomości do jej obiektów docelowych, a nie transferuje własność aktualnie przechowywanego komunikatu.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `overwrite_buffer` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zużywanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale jest zawsze poprzedzone wywołaniem `reserve`.

## <a name="has_value"></a>has_value

Sprawdza, czy ten blok `overwrite_buffer` Messaging ma jeszcze wartość.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli blok odebrał wartość, w przeciwnym razie **false** .

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `overwrite_buffer`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="dtor"></a>~ overwrite_buffer

Niszczy blok komunikatów `overwrite_buffer`.

```cpp
~overwrite_buffer();
```

## <a name="ctor"></a>overwrite_buffer

Tworzy blok komunikatów `overwrite_buffer`.

```cpp
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `overwrite_buffer`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `overwrite_buffer`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `filter_method` to Funktor z sygnaturą `bool (T const &)`, która jest wywoływana przez ten blok komunikatów `overwrite_buffer` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `overwrite_buffer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
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

Umieszcza `message _PMessage` w tym bloku komunikatów `overwrite_buffer` i oferuje go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`, do którego `overwrite_buffer` przejąć własność.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje bieżący komunikat w `overwrite_buffer` przy użyciu nowo zaakceptowanego `_PMessage`komunikatów.

## <a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `overwrite_buffer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
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

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , ponieważ blok nie odkłada proponowanych komunikatów.

## <a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

## <a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `overwrite_buffer`.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` obiektu `message`, który jest zarezerwowany.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli komunikat został pomyślnie zarezerwowany, w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve`, jeśli zwraca **wartość true**, należy wywołać `consume` lub `release`, aby przejąć lub zwolnić własność wiadomości.

## <a name="resume_propagation"></a>resume_propagation

Wznawia propagację po wydaniu rezerwacji.

```cpp
virtual void resume_propagation();
```

## <a name="value"></a>wartościami

Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w bloku komunikatów `overwrite_buffer`.

```cpp
T value();
```

### <a name="return-value"></a>Wartość zwrócona

Ładunek obecnie przechowywanego komunikatu.

### <a name="remarks"></a>Uwagi

Wartość przechowywana w `overwrite_buffer` może ulec zmianie natychmiast po powrocie tej metody. Ta metoda będzie czekać, aż zostanie wyświetlony komunikat, jeśli w `overwrite_buffer`nie zostanie zapisany żaden komunikat.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[unbounded_buffer, klasa](unbounded-buffer-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
