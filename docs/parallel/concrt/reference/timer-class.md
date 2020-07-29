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
ms.openlocfilehash: 026aef03bb813585decb206c1691835330a4dd05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224945"
---
# <a name="timer-class"></a>Klasa czasomierza

`timer`Blok komunikatów to jeden obiekt docelowy, który `source_block` umożliwia wysyłanie wiadomości do jej obiektu docelowego po upływie określonego czasu lub w określonych odstępach czasu.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów wyjściowych tego bloku.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[licz](#ctor)|Przeciążone. Tworzy `timer` blok komunikatów, który będzie uruchamiał dany komunikat po upływie określonego interwału.|
|[~ Timer — destruktor](#dtor)|Niszczy `timer` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[została](#pause)|Kończy `timer` blok komunikatów. Jeśli jest to powtarzalny `timer` blok komunikatów, można go uruchomić ponownie przy użyciu kolejnego `start()` wywołania. W przypadku niepowtarzalnych czasomierzy ma to taki sam skutek jak `stop` wywołanie.|
|[start](#start)|Uruchamia `timer` blok komunikatów. Określona liczba milisekund po wywołaniu tej wartości zostanie przepropagowana w dół jako `message` .|
|[komunikat](#stop)|Kończy `timer` blok komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten `timer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `timer` i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `timer` blokiem obsługi komunikatów.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Próbuje zaoferować komunikat utworzony przez `timer` blok ze wszystkimi połączonymi obiektami docelowymi.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten `timer` blok komunikatów. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
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

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten `timer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `timer` i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.

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

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `timer` blokiem obsługi komunikatów.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="pause"></a><a name="pause"></a>została

Kończy `timer` blok komunikatów. Jeśli jest to powtarzalny `timer` blok komunikatów, można go uruchomić ponownie przy użyciu kolejnego `start()` wywołania. W przypadku niepowtarzalnych czasomierzy ma to taki sam skutek jak `stop` wywołanie.

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Próbuje zaoferować komunikat utworzony przez `timer` blok ze wszystkimi połączonymi obiektami docelowymi.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten `timer` blok komunikatów.

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

## <a name="start"></a><a name="start"></a>Start

Uruchamia `timer` blok komunikatów. Określona liczba milisekund po wywołaniu tej wartości zostanie przepropagowana w dół jako `message` .

```cpp
void start();
```

## <a name="stop"></a><a name="stop"></a>komunikat

Kończy `timer` blok komunikatów.

```cpp
void stop();
```

## <a name="timer"></a><a name="ctor"></a>licz

Tworzy `timer` blok komunikatów, który będzie uruchamiał dany komunikat po upływie określonego interwału.

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

*wartościami*<br/>
Wartość, która zostanie propagowana po upływie czasu czasomierza.

*_PTarget*<br/>
Obiekt docelowy, do którego czasomierz będzie propagowany wiadomości.

*_Repeating*<br/>
W przypadku wartości true wskazuje, że czasomierz będzie okresowo uruchamiać co `_Ms` milisekundy.

*_Scheduler*<br/>
`Scheduler`Zaplanowano obiekt, w którym zaplanowano zadanie propagacji dla `timer` bloku obsługi komunikatów.

*_ScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `timer` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_Scheduler` `_ScheduleGroup` parametrów lub.

## <a name="timer"></a><a name="dtor"></a>~ Czasomierz

Niszczy `timer` blok komunikatów.

```cpp
~timer();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
