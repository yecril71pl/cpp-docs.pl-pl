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
ms.openlocfilehash: 436d0d4cc16ee18449178782b775a25bb1d8592a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159915"
---
# <a name="singleassignment-class"></a>Klasa single_assignment

A `single_assignment` blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać jeden zapis — po `message`.

## <a name="syntax"></a>Składnia

```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatu przechowywane i rozprowadzane przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[single_assignment](#ctor)|Przeciążone. Konstruuje `single_assignment` Blok obsługi wiadomości.|
|[~ single_assignment — destruktor](#dtor)|Niszczy `single_assignment` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy to `single_assignment` Blok obsługi wiadomości został zainicjowany z wartością jeszcze.|
|[value](#value)|Pobiera referencję do bieżącego ładunku komunikatów znajdujących się w `single_assignment` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `single_assignment` Blok obsługi wiadomości, zwracając kopię wiadomości do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `single_assignment` i zastrzeżonych przez element docelowy, zwracając kopię wiadomości do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `single_assignment` Blok obsługi wiadomości.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `single_assignment` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym `single_assignment` bloku komunikatów i oferuje go do wszystkich połączonych elementów docelowych.|
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `single_assignment` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `single_assignment` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|

## <a name="remarks"></a>Uwagi

A `single_assignment` Blok obsługi wiadomości propaguje kopie komunikat do każdego obiektu docelowego.

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[Itarget —](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept_message"></a> accept_message

Akceptuje wiadomości, które było oferowane przez to `single_assignment` Blok obsługi wiadomości, zwracając kopię wiadomości do obiektu wywołującego.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

`single_assignment` Komunikatów bloku kopie zwraca komunikat do jego obiekty docelowe, zamiast przenoszenia własności obecnie konsekwencje na gruncie komunikatu.

##  <a name="consume_message"></a> consume_message

Wykorzystuje komunikat, który został poprzednio oferowana przez `single_assignment` i zastrzeżonych przez element docelowy, zwracając kopię wiadomości do obiektu wywołującego.

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

##  <a name="has_value"></a> has_value —

Sprawdza, czy to `single_assignment` Blok obsługi wiadomości został zainicjowany z wartością jeszcze.

```
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** odebranie bloku ma wartość **false** inaczej.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `single_assignment` Blok obsługi wiadomości.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączone obiektu docelowego.

##  <a name="propagate_message"></a> propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `single_assignment` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Umieszcza `message` `_PMessage` w tym `single_assignment` bloku komunikatów i oferuje go do wszystkich połączonych elementów docelowych.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` że `single_assignment` Blok obsługi wiadomości miało własności.

##  <a name="release_message"></a> release_message

Zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="reserve_message"></a> reserve_message

Zarezerwowaniu wiadomości przez oferowane wcześniej to `single_assignment` Blok obsługi wiadomości.

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

##  <a name="send_message"></a> send_message

Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `single_assignment` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="ctor"></a> single_assignment

Konstruuje `single_assignment` Blok obsługi wiadomości.

```
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
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `single_assignment` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `single_assignment` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Typ `filter_method` jest funktor za pomocą podpisu `bool (T const &)` który zostanie wywołany przez to `single_assignment` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.

##  <a name="dtor"></a> ~ single_assignment

Niszczy `single_assignment` Blok obsługi wiadomości.

```
~single_assignment();
```

##  <a name="value"></a> Wartość

Pobiera referencję do bieżącego ładunku komunikatów znajdujących się w `single_assignment` Blok obsługi wiadomości.

```
T const& value();
```

### <a name="return-value"></a>Wartość zwracana

Ładunek przechowywanych wiadomości.

### <a name="remarks"></a>Uwagi

Ta metoda czeka na zakończenie nadejścia wiadomości, jeśli żaden komunikat nie jest obecnie przechowywanych w `single_assignment` Blok obsługi wiadomości.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[overwrite_buffer, klasa](overwrite-buffer-class.md)<br/>
[unbounded_buffer, klasa](unbounded-buffer-class.md)
