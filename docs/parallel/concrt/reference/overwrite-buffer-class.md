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
ms.openlocfilehash: 680c07015538a2eacc9480d3cd22da9a36071e32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456007"
---
# <a name="overwritebuffer-class"></a>Klasa overwrite_buffer

`overwrite_buffer` Blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać pojedynczej wiadomości w czasie. Nowe komunikaty zastąpienie wcześniej konsekwencje na gruncie z nich.

## <a name="syntax"></a>Składnia

```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów przechowywane i rozprowadzane przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Przeciążone. Konstruuje `overwrite_buffer` Blok obsługi wiadomości.|
|[~overwrite_buffer Destructor](#dtor)|Niszczy `overwrite_buffer` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy to `overwrite_buffer` Blok obsługi wiadomości nie został jeszcze wartość.|
|[value](#value)|Pobiera referencję do bieżącego ładunku komunikatów znajdujących się w `overwrite_buffer` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `overwrite_buffer` Blok obsługi wiadomości, zwracając kopię wiadomości do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `overwrite_buffer` bloku komunikatów i zastrzeżona przez element docelowy, zwracając kopię wiadomości do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `overwrite_buffer` Blok obsługi wiadomości.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `overwrite_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym `overwrite_buffer` bloku komunikatów i oferuje go do wszystkich połączonych elementów docelowych.|
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `overwrite_buffer` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `overwrite_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [itarget::supports_anonymous_source —](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

`overwrite_buffer` Blok obsługi wiadomości propaguje kopii przechowywanej komunikat do każdego z jego elementów docelowych.

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[Itarget —](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept_message"></a> accept_message

Akceptuje wiadomości, które było oferowane przez to `overwrite_buffer` Blok obsługi wiadomości, zwracając kopię wiadomości do obiektu wywołującego.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

`overwrite_buffer` Komunikatów bloku kopie zwraca komunikat do jego obiekty docelowe, zamiast przenoszenia własności obecnie konsekwencje na gruncie komunikatu.

##  <a name="consume_message"></a> consume_message

Wykorzystuje komunikat, który został poprzednio oferowana przez `overwrite_buffer` bloku komunikatów i zastrzeżona przez element docelowy, zwracając kopię wiadomości do obiektu wywołującego.

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

Sprawdza, czy to `overwrite_buffer` Blok obsługi wiadomości nie został jeszcze wartość.

```
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** odebranie bloku ma wartość **false** inaczej.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `overwrite_buffer` Blok obsługi wiadomości.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączone obiektu docelowego.

##  <a name="dtor"></a> ~overwrite_buffer

Niszczy `overwrite_buffer` Blok obsługi wiadomości.

```
~overwrite_buffer();
```

##  <a name="ctor"></a> overwrite_buffer

Konstruuje `overwrite_buffer` Blok obsługi wiadomości.

```
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

*_Filtruj*<br/>
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `overwrite_buffer` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `overwrite_buffer` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Typ `filter_method` jest funktor za pomocą podpisu `bool (T const &)` który zostanie wywołany przez to `overwrite_buffer` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.

##  <a name="propagate_message"></a> propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `overwrite_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

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

Umieszcza `message _PMessage` w tym `overwrite_buffer` bloku komunikatów i oferuje go do wszystkich połączonych elementów docelowych.

```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu że `overwrite_buffer` miało własności.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje do bieżącej wiadomości w `overwrite_buffer` komunikatem nowo odebrane `_PMessage`.

##  <a name="send_message"></a> send_message

Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `overwrite_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

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

##  <a name="supports_anonymous_source"></a> supports_anonymous_source —

Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** ponieważ bloku nie odłożyć dostępne komunikaty.

##  <a name="release_message"></a> release_message

Zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="reserve_message"></a> reserve_message

Zarezerwowaniu wiadomości przez oferowane wcześniej to `overwrite_buffer` Blok obsługi wiadomości.

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

##  <a name="value"></a> Wartość

Pobiera referencję do bieżącego ładunku komunikatów znajdujących się w `overwrite_buffer` Blok obsługi wiadomości.

```
T value();
```

### <a name="return-value"></a>Wartość zwracana

Obciążenie komunikatu aktualnie przechowywana.

### <a name="remarks"></a>Uwagi

Wartość przechowywana we `overwrite_buffer` można zmienić natychmiast, po powrocie z tej metody. Ta metoda czeka na zakończenie nadejścia wiadomości, jeśli żaden komunikat nie jest obecnie przechowywanych w `overwrite_buffer`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa unbounded_buffer](unbounded-buffer-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
