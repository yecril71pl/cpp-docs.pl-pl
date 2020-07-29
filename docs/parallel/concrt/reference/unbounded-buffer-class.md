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
ms.openlocfilehash: e02fa1ffbf4c3e2c7d17dfe2d6ae66758945d9de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219523"
---
# <a name="unbounded_buffer-class"></a>Klasa unbounded_buffer

`unbounded_buffer`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania nieograniczonej liczby komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>Parametry

*_Type*<br/>
Typ ładunku komunikatów przechowywanych i propagowanych przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Przeciążone. Tworzy `unbounded_buffer` blok komunikatów.|
|[~ unbounded_buffer destruktor](#dtor)|Niszczy `unbounded_buffer` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[z kolejki](#dequeue)|Usuwa element z `unbounded_buffer` bloku obsługi komunikatów.|
|[dodawania](#enqueue)|Dodaje element do `unbounded_buffer` bloku obsługi komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten `unbounded_buffer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `unbounded_buffer` blok komunikatów i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `unbounded_buffer` blokiem obsługi komunikatów.|
|[process_input_messages](#process_input_messages)|Umieszcza `message` `_PMessage` w tym `unbounded_buffer` bloku komunikatów i próbuje zaoferować go wszystkim połączonym obiektom docelowym.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.|
|[propagate_output_messages](#propagate_output_messages)|Umieszcza `message` `_PMessage` w tym `unbounded_buffer` bloku komunikatów i próbuje zaoferować go wszystkim połączonym obiektom docelowym. (Zastępuje [source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten `unbounded_buffer` blok komunikatów. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten `unbounded_buffer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `unbounded_buffer` blok komunikatów i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Używany obiekt.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Przypomina `accept` , ale jest zawsze poprzedzone wywołaniem do `reserve` .

## <a name="dequeue"></a><a name="dequeue"></a>z kolejki

Usuwa element z `unbounded_buffer` bloku obsługi komunikatów.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Wartość zwracana

Ładunek wiadomości został usunięty z `unbounded_buffer` .

## <a name="enqueue"></a><a name="enqueue"></a>dodawania

Dodaje element do `unbounded_buffer` bloku obsługi komunikatów.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parametry

*_Item*<br/>
Element do dodania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli element został zaakceptowany, **`false`** w przeciwnym razie.

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `unbounded_buffer` blokiem obsługi komunikatów.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md#message_status) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

Umieszcza `message` `_PMessage` w tym `unbounded_buffer` bloku komunikatów i próbuje zaoferować go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Uwagi

Jeśli inny komunikat jest już wcześniejszy niż ten, w `unbounded_buffer` , Propagacja do połączonych obiektów docelowych nie nastąpi do momentu zaakceptowania lub użycia jakichkolwiek wcześniejszych komunikatów. Pierwszy połączony element docelowy został pomyślnie `accept` lub `consume` komunikat ma własność, a żaden inny element docelowy nie może uzyskać komunikatu.

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

Umieszcza `message` `_PMessage` w tym `unbounded_buffer` bloku komunikatów i próbuje zaoferować go wszystkim połączonym obiektom docelowym.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, która ma zostać przetworzona.

## <a name="release_message"></a><a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten `unbounded_buffer` blok komunikatów.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

Synchronicznie przekazuje komunikat z `ISource` bloku do tego `unbounded_buffer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md#message_status) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** ponieważ blok nie odkłada proponowanych komunikatów.

## <a name="unbounded_buffer"></a><a name="ctor"></a>unbounded_buffer

Tworzy `unbounded_buffer` blok komunikatów.

```cpp
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
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `unbounded_buffer` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `unbounded_buffer` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Typ `filter_method` to Funktor z podpisem `bool (_Type const &)` , który jest wywoływany przez ten `unbounded_buffer` blok komunikatów, aby określić, czy powinien on akceptować oferowany komunikat.

## <a name="unbounded_buffer"></a><a name="dtor"></a>~ unbounded_buffer

Niszczy `unbounded_buffer` blok komunikatów.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa overwrite_buffer](overwrite-buffer-class.md)<br/>
[Klasa single_assignment](single-assignment-class.md)
