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
ms.openlocfilehash: beb374efe26c25fed490b7407e087e2cc46043c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659839"
---
# <a name="timer-class"></a>Klasa czasomierza

A `timer` blok komunikatów jest celu pojedynczego `source_block` zdolne do wysyłania komunikatu do jego element docelowy po określonym okresie czasu lub w określonych odstępach czasu.

## <a name="syntax"></a>Składnia

```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów wyjściowych w tym bloku.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czasomierz](#ctor)|Przeciążone. Konstruuje `timer` blok komunikatów, który zostanie uruchomiony z podanym komunikatem po upływie określonego czasu.|
|[~ timer — destruktor](#dtor)|Niszczy `timer` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wstrzymaj](#pause)|Zatrzymuje `timer` Blok obsługi wiadomości. Jeśli jest powtarzanej `timer` komunikatów bloku, je można ponownie uruchomić z kolejnej `start()` wywołania. Powtarzalnych czasomierze, ma taki sam skutek jak `stop` wywołania.|
|[start](#start)|Uruchamia `timer` Blok obsługi wiadomości. Nosi nazwę określoną liczbę milisekund, po to, określona wartość będzie propagowane podrzędnego jako `message`.|
|[Zatrzymaj](#stop)|Zatrzymuje `timer` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `timer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `timer` i zastrzeżonych przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `timer` Blok obsługi wiadomości.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Zaoferować komunikat generowany przez `timer` bloku do wszystkich połączonych elementów docelowych.|
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `timer` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept_message"></a> accept_message

Akceptuje wiadomości, które było oferowane przez to `timer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

##  <a name="consume_message"></a> consume_message

Wykorzystuje komunikat, który został poprzednio oferowana przez `timer` i zastrzeżonych przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu są używane.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `timer` Blok obsługi wiadomości.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączone obiektu docelowego.

##  <a name="pause"></a> Wstrzymaj

Zatrzymuje `timer` Blok obsługi wiadomości. Jeśli jest powtarzanej `timer` komunikatów bloku, je można ponownie uruchomić z kolejnej `start()` wywołania. Powtarzalnych czasomierze, ma taki sam skutek jak `stop` wywołania.

```
void pause();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Zaoferować komunikat generowany przez `timer` bloku do wszystkich połączonych elementów docelowych.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

##  <a name="release_message"></a> release_message

Zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="reserve_message"></a> reserve_message

Zarezerwowaniu wiadomości przez oferowane wcześniej to `timer` Blok obsługi wiadomości.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli komunikat został pomyślnie zarezerwowany, **false** inaczej.

### <a name="remarks"></a>Uwagi

Po `reserve` jest wywoływana, jeśli zwróci ona **true**, albo `consume` lub `release` musi zostać wywołana wersji własności wiadomości lub wykonać.

##  <a name="resume_propagation"></a> resume_propagation

Wznawia działanie propagacji, po udostępnieniu rezerwacji.

```
virtual void resume_propagation();
```

##  <a name="start"></a> Rozpocznij

Uruchamia `timer` Blok obsługi wiadomości. Nosi nazwę określoną liczbę milisekund, po to, określona wartość będzie propagowane podrzędnego jako `message`.

```
void start();
```

##  <a name="stop"></a> Zatrzymaj

Zatrzymuje `timer` Blok obsługi wiadomości.

```
void stop();
```

##  <a name="ctor"></a> Czasomierz

Konstruuje `timer` blok komunikatów, który zostanie uruchomiony z podanym komunikatem po upływie określonego czasu.

```
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
Liczba milisekund, które muszą upłynąć od wywołanie metody start do podrzędne propagowane określonej wiadomości.

*value*<br/>
Wartość, która będzie propagowane podrzędne po upływie czasomierza.

*_PTarget*<br/>
Obiekt docelowy, do którego czasomierza rozpropaguje komunikat.

*_Repeating*<br/>
W przypadku opcji true wskazuje, że uruchomienie czasomierza nastąpi okresowo co `_Ms` milisekund.

*_Scheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `timer` zaplanowano blok komunikatów jest zaplanowane.

*_ScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `timer` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_Scheduler` lub `_ScheduleGroup` parametrów.

##  <a name="dtor"></a> ~ czasomierza

Niszczy `timer` Blok obsługi wiadomości.

```
~timer();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
