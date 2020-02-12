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
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142737"
---
# <a name="single_assignment-class"></a>Klasa single_assignment

Blok obsługi komunikatów `single_assignment` to wieloobiektowa, uporządkowana `propagator_block`, która umożliwia przechowywanie pojedynczego `message`jednokrotnego zapisu.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku wiadomości przechowywanej i propagowany przez bufor.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[single_assignment](#ctor)|Przeciążone. Tworzy blok komunikatów `single_assignment`.|
|[~ single_assignment destruktor](#dtor)|Niszczy blok komunikatów `single_assignment`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy ten blok komunikatów `single_assignment` został jeszcze zainicjowany z wartością.|
|[value](#value)|Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w bloku komunikatów `single_assignment`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `single_assignment`, zwracając kopię komunikatu do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `single_assignment` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `single_assignment`.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `single_assignment`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym bloku komunikatów `single_assignment` i oferuje go wszystkim połączonym obiektom docelowym.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `single_assignment`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `single_assignment`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|

## <a name="remarks"></a>Uwagi

Blok `single_assignment` Messaging propaguje kopie wiadomości do każdego obiektu docelowego.

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

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `single_assignment`, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Blok komunikatów `single_assignment` zwraca kopie wiadomości do jej obiektów docelowych, a nie transferuje własność aktualnie przechowywanego komunikatu.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `single_assignment` i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.

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

Sprawdza, czy ten blok komunikatów `single_assignment` został jeszcze zainicjowany z wartością.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli blok odebrał wartość, w przeciwnym razie **false** .

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `single_assignment`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `single_assignment`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

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

Umieszcza `_PMessage` `message` w tym bloku komunikatów `single_assignment` i oferuje go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message`, że ten blok komunikatów `single_assignment` ma przejmować własność.

## <a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

## <a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `single_assignment`.

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

## <a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `single_assignment`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

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

## <a name="ctor"></a>single_assignment

Tworzy blok komunikatów `single_assignment`.

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
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `single_assignment`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `single_assignment`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `filter_method` to Funktor z sygnaturą `bool (T const &)`, która jest wywoływana przez ten blok komunikatów `single_assignment` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="dtor"></a>~ single_assignment

Niszczy blok komunikatów `single_assignment`.

```cpp
~single_assignment();
```

## <a name="value"></a>wartościami

Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w bloku komunikatów `single_assignment`.

```cpp
T const& value();
```

### <a name="return-value"></a>Wartość zwrócona

Ładunek przechowywanej wiadomości.

### <a name="remarks"></a>Uwagi

Ta metoda będzie czekać, aż zostanie wyświetlony komunikat, jeśli w bloku `single_assignment` Messaging nie zostanie zapisany żaden komunikat.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[overwrite_buffer, klasa](overwrite-buffer-class.md)<br/>
[unbounded_buffer, klasa](unbounded-buffer-class.md)
