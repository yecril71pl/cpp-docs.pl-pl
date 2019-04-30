---
title: Klasa unbounded_buffer
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: 1474381a2d1c0947b2428ab4cf0b4683198eef84
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407838"
---
# <a name="unboundedbuffer-class"></a>Klasa unbounded_buffer

`unbounded_buffer` Blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać nieograniczoną liczbę komunikatów.

## <a name="syntax"></a>Składnia

```
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

#### <a name="parameters"></a>Parametry

*_Typ*<br/>
Typ ładunku komunikatów przechowywane i rozprowadzane przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Przeciążone. Konstruuje `unbounded_buffer` Blok obsługi wiadomości.|
|[~ unbounded_buffer — destruktor](#dtor)|Niszczy `unbounded_buffer` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń z kolejki](#dequeue)|Usuwa element z `unbounded_buffer` Blok obsługi wiadomości.|
|[enqueue](#enqueue)|Dodaje element do `unbounded_buffer` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `unbounded_buffer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `unbounded_buffer` bloku komunikatów i zastrzeżona przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `unbounded_buffer` Blok obsługi wiadomości.|
|[process_input_messages](#process_input_messages)|Umieszcza `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje zaoferować ją do wszystkich połączonych elementów docelowych.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `unbounded_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[propagate_output_messages](#propagate_output_messages)|Umieszcza `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje zaoferować ją do wszystkich połączonych elementów docelowych. (Przesłania [source_block::propagate_output_messages —](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `unbounded_buffer` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `unbounded_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [itarget::supports_anonymous_source —](itarget-class.md#supports_anonymous_source).)|

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[Itarget —](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept_message"></a> accept_message

Akceptuje wiadomości, które było oferowane przez to `unbounded_buffer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.

```
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

##  <a name="consume_message"></a> consume_message

Wykorzystuje komunikat, który został poprzednio oferowana przez `unbounded_buffer` bloku komunikatów i zastrzeżona przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu są używane.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.

##  <a name="dequeue"></a> Usuń z kolejki

Usuwa element z `unbounded_buffer` Blok obsługi wiadomości.

```
_Type dequeue();
```

### <a name="return-value"></a>Wartość zwracana

Ładunek komunikatu usunięte z `unbounded_buffer`.

##  <a name="enqueue"></a> Umieścić w kolejce

Dodaje element do `unbounded_buffer` Blok obsługi wiadomości.

```
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parametry

*_Element*<br/>
Element do dodania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli element został zaakceptowany, **false** inaczej.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `unbounded_buffer` Blok obsługi wiadomości.

```
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączone obiektu docelowego.

##  <a name="propagate_message"></a> propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `unbounded_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md#message_status) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="propagate_output_messages"></a> propagate_output_messages

Umieszcza `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje zaoferować ją do wszystkich połączonych elementów docelowych.

```
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Uwagi

Jeśli inny komunikat o błędzie jest już wcześniej wskazanego w `unbounded_buffer`, nie nastąpi propagacji do połączonych elementów docelowych, dopóki wszystkie wcześniejsze komunikaty zostały zaakceptowane lub używane. Pierwszy łączenie urządzenie pod docelowym zakończyło się pomyślnie `accept` lub `consume` komunikat przejmuje na własność i żadne miejsce docelowe mogą następnie uzyskać komunikat.

##  <a name="process_input_messages"></a> process_input_messages —

Umieszcza `message` `_PMessage` w tym `unbounded_buffer` Blok obsługi wiadomości i próbuje zaoferować ją do wszystkich połączonych elementów docelowych.

```
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być przetwarzane.

##  <a name="release_message"></a> release_message

Zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="reserve_message"></a> reserve_message

Zarezerwowaniu wiadomości przez oferowane wcześniej to `unbounded_buffer` Blok obsługi wiadomości.

```
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `unbounded_buffer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md#message_status) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source —

Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** ponieważ bloku nie odłożyć dostępne komunikaty.

##  <a name="ctor"></a> unbounded_buffer

Konstruuje `unbounded_buffer` Blok obsługi wiadomości.

```
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `unbounded_buffer` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `unbounded_buffer` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Typ `filter_method` jest funktor za pomocą podpisu `bool (_Type const &)` który zostanie wywołany przez to `unbounded_buffer` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.

##  <a name="dtor"></a> ~ unbounded_buffer

Niszczy `unbounded_buffer` Blok obsługi wiadomości.

```
~unbounded_buffer();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[overwrite_buffer, klasa](overwrite-buffer-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
