---
title: Klasa single_assignment
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 6b92508c81311774816e804eb36ac8fbfb2aa82b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219563"
---
# <a name="single_assignment-class"></a>Klasa single_assignment

`single_assignment`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania jednego, jednokrotnego zapisu `message` .

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku wiadomości przechowywanej i propagowany przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[single_assignment](#ctor)|Przeciążone. Tworzy `single_assignment` blok komunikatów.|
|[~ single_assignment destruktor](#dtor)|Niszczy `single_assignment` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy ten `single_assignment` blok komunikatów został jeszcze zainicjowany z wartością.|
|[wartościami](#value)|Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w `single_assignment` bloku obsługi komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten `single_assignment` blok komunikatów, zwracając kopię komunikatu do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `single_assignment` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `single_assignment` blokiem obsługi komunikatów.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym `single_assignment` bloku komunikatów i oferuje go wszystkim połączonym obiektom docelowym.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten `single_assignment` blok komunikatów. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.|

## <a name="remarks"></a>Uwagi

`single_assignment`Blok komunikatów propaguje kopie wiadomości do każdego obiektu docelowego.

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten `single_assignment` blok komunikatów, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

`single_assignment`Blok komunikatów zwraca kopie wiadomości do jej obiektów docelowych, a nie transferuje własność aktualnie przechowywanego komunikatu.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `single_assignment` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Używany obiekt.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Przypomina `accept` , ale jest zawsze poprzedzone wywołaniem do `reserve` .

## <a name="has_value"></a><a name="has_value"></a>has_value

Sprawdza, czy ten `single_assignment` blok komunikatów został jeszcze zainicjowany z wartością.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli blok odebrał wartość, **`false`** w przeciwnym razie.

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `single_assignment` blokiem obsługi komunikatów.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Umieszcza `message` `_PMessage` w tym `single_assignment` bloku komunikatów i oferuje go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do tego `message` `single_assignment` bloku obsługi komunikatów przejmuje własność.

## <a name="release_message"></a><a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten `single_assignment` blok komunikatów.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Obiekt, który jest `runtime_object_identity` `message` zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Po `reserve` wywołaniu, jeśli zwróci **`true`** , `consume` lub `release` musi zostać wywołana w celu podjęcia lub zwolnienia własności wiadomości.

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

Wznawia propagację po wydaniu rezerwacji.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a><a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z `ISource` bloku do tego `single_assignment` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="single_assignment"></a><a name="ctor"></a>single_assignment

Tworzy `single_assignment` blok komunikatów.

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `single_assignment` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `single_assignment` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Typ `filter_method` to Funktor z podpisem `bool (T const &)` , który jest wywoływany przez ten `single_assignment` blok komunikatów, aby określić, czy powinien on akceptować oferowany komunikat.

## <a name="single_assignment"></a><a name="dtor"></a>~ single_assignment

Niszczy `single_assignment` blok komunikatów.

```cpp
~single_assignment();
```

## <a name="value"></a><a name="value"></a>wartościami

Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w `single_assignment` bloku obsługi komunikatów.

```cpp
T const& value();
```

### <a name="return-value"></a>Wartość zwracana

Ładunek przechowywanej wiadomości.

### <a name="remarks"></a>Uwagi

Ta metoda będzie oczekiwać do momentu odebrania komunikatu, jeśli w bloku obsługi komunikatów nie jest aktualnie przechowywany żaden komunikat `single_assignment` .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa overwrite_buffer](overwrite-buffer-class.md)<br/>
[Klasa unbounded_buffer](unbounded-buffer-class.md)
