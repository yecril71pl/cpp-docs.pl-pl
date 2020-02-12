---
title: Klasa czasomierza
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: c39afc565a7ec775600b9c9fb6f15a89acdef57b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142527"
---
# <a name="timer-class"></a>Klasa czasomierza

Blok komunikatów `timer` jest `source_block`, który umożliwia wysyłanie wiadomości do jej obiektu docelowego po upływie określonego czasu lub w określonych odstępach czasu.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku komunikatów wyjściowych tego bloku.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[licz](#ctor)|Przeciążone. Konstruuje blok `timer` Messaging, który będzie uruchamiał dany komunikat po upływie określonego interwału.|
|[~ Timer — destruktor](#dtor)|Niszczy blok komunikatów `timer`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[została](#pause)|Kończy blok komunikatów `timer`. Jeśli jest to powtarzalny blok komunikatów `timer`, można go uruchomić ponownie przy użyciu kolejnego wywołania `start()`. W przypadku niepowtarzalnych czasomierzy ma to taki sam skutek jak wywołanie `stop`.|
|[start](#start)|Uruchamia blok komunikatów `timer`. Określona liczba milisekund po wywołaniu tej wartości zostanie przepropagowana w dół jako `message`.|
|[komunikat](#stop)|Kończy blok komunikatów `timer`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `timer`, przekazując własność do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `timer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `timer`.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Próbuje zaoferować komunikat utworzony przez blok `timer` do wszystkich połączonych obiektów docelowych.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `timer`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `timer`, przekazując własność do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `timer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.

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

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `timer`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="pause"></a>została

Kończy blok komunikatów `timer`. Jeśli jest to powtarzalny blok komunikatów `timer`, można go uruchomić ponownie przy użyciu kolejnego wywołania `start()`. W przypadku niepowtarzalnych czasomierzy ma to taki sam skutek jak wywołanie `stop`.

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Próbuje zaoferować komunikat utworzony przez blok `timer` do wszystkich połączonych obiektów docelowych.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `timer`.

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

## <a name="start"></a>Start

Uruchamia blok komunikatów `timer`. Określona liczba milisekund po wywołaniu tej wartości zostanie przepropagowana w dół jako `message`.

```cpp
void start();
```

## <a name="stop"></a>komunikat

Kończy blok komunikatów `timer`.

```cpp
void stop();
```

## <a name="ctor"></a>licz

Konstruuje blok `timer` Messaging, który będzie uruchamiał dany komunikat po upływie określonego interwału.

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>Parametry

*_Ms*<br/>
Liczba milisekund, które muszą upłynąć po wywołaniu dla określonego komunikatu, który ma zostać propagowany.

*value*<br/>
Wartość, która zostanie propagowana po upływie czasu czasomierza.

*_PTarget*<br/>
Obiekt docelowy, do którego czasomierz będzie propagowany wiadomości.

*_Repeating*<br/>
W przypadku wartości true wskazuje, że czasomierz będzie okresowo uruchamiać co `_Ms` milisekund.

*_Scheduler*<br/>
Zaplanowano `Scheduler` obiektu, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `timer`.

*_ScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `timer`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_Scheduler` lub `_ScheduleGroup`.

## <a name="dtor"></a>~ Czasomierz

Niszczy blok komunikatów `timer`.

```cpp
~timer();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
