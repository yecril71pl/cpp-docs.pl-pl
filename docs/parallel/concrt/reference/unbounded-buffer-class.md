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
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142332"
---
# <a name="unbounded_buffer-class"></a>Klasa unbounded_buffer

Blok komunikatów `unbounded_buffer` to wiele obiektów, które mają uporządkowane `propagator_block` z możliwością przechowywania nieograniczonej liczby komunikatów.

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

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Przeciążone. Tworzy blok komunikatów `unbounded_buffer`.|
|[~ unbounded_buffer destruktor](#dtor)|Niszczy blok komunikatów `unbounded_buffer`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[z kolejki](#dequeue)|Usuwa element z bloku obsługi komunikatów `unbounded_buffer`.|
|[dodawania](#enqueue)|Dodaje element do bloku obsługi komunikatów `unbounded_buffer`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `unbounded_buffer`, przekazując własność do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `unbounded_buffer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `unbounded_buffer`.|
|[process_input_messages](#process_input_messages)|Umieszcza `_PMessage` `message` w tym bloku komunikatów `unbounded_buffer` i próbuje zaoferować go wszystkim połączonym obiektom docelowym.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `unbounded_buffer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[propagate_output_messages](#propagate_output_messages)|Umieszcza `_PMessage` `message` w tym bloku komunikatów `unbounded_buffer` i próbuje zaoferować go wszystkim połączonym obiektom docelowym. (Zastępuje [source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `unbounded_buffer`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `unbounded_buffer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

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

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `unbounded_buffer`, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez blok komunikatów `unbounded_buffer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zużywanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale jest zawsze poprzedzone wywołaniem `reserve`.

## <a name="dequeue"></a>z kolejki

Usuwa element z bloku obsługi komunikatów `unbounded_buffer`.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Wartość zwrócona

Ładunek komunikatu został usunięty z `unbounded_buffer`.

## <a name="enqueue"></a>dodawania

Dodaje element do bloku obsługi komunikatów `unbounded_buffer`.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parametry

*_Item*<br/>
Element do dodania.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli element został zaakceptowany, w przeciwnym razie **zwraca wartość false** .

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `unbounded_buffer`.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `unbounded_buffer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md#message_status) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_output_messages"></a>propagate_output_messages

Umieszcza `_PMessage` `message` w tym bloku komunikatów `unbounded_buffer` i próbuje zaoferować go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Uwagi

Jeśli inny komunikat jest już wcześniej w `unbounded_buffer`, Propagacja do połączonych obiektów docelowych nie będzie wykonywana do momentu zaakceptowania lub użycia jakichkolwiek wcześniejszych komunikatów. Pierwszy połączony obiekt docelowy, który został pomyślnie `accept` lub `consume` komunikat ma własność, a żaden inny element docelowy nie może uzyskać komunikatu.

## <a name="process_input_messages"></a>process_input_messages

Umieszcza `_PMessage` `message` w tym bloku komunikatów `unbounded_buffer` i próbuje zaoferować go wszystkim połączonym obiektom docelowym.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, która ma zostać przetworzona.

## <a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

## <a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `unbounded_buffer`.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `unbounded_buffer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md#message_status) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , ponieważ blok nie odkłada proponowanych komunikatów.

## <a name="ctor"></a>unbounded_buffer

Tworzy blok komunikatów `unbounded_buffer`.

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
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `unbounded_buffer`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `unbounded_buffer`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `filter_method` to Funktor z sygnaturą `bool (_Type const &)`, która jest wywoływana przez ten blok komunikatów `unbounded_buffer` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="dtor"></a>~ unbounded_buffer

Niszczy blok komunikatów `unbounded_buffer`.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[overwrite_buffer, klasa](overwrite-buffer-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
