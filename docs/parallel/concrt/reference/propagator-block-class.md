---
title: propagator_block — Klasa
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138745"
---
# <a name="propagator_block-class"></a>propagator_block — Klasa

Klasa `propagator_block` jest abstrakcyjną klasą bazową dla bloków komunikatów, które są zarówno źródłowym, jak i docelowym. Łączy ona funkcje obu klas `source_block` i `target_block`.

## <a name="syntax"></a>Składnia

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Rejestr łącza, który ma być używany do przechowywania linków docelowych.

*_SourceLinkRegistry*<br/>
Rejestr łącza, który ma być używany do przechowywania linków źródłowych.

*_MessageProcessorType*<br/>
Typ procesora do przetwarzania komunikatów.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`source_iterator`|Typ iteratora dla `source_link_manager` dla tego `propagator_block`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[propagator_block](#ctor)|Konstruuje obiekt `propagator_block`.|
|[~ propagator_block destruktor](#dtor)|Niszczy obiekt `propagator_block`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[rozpowszechni](#propagate)|Asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|
|[Wyślij](#send)|Synchronicznie inicjuje komunikat do tego bloku. Wywoływane przez blok `ISource`. Gdy ta funkcja zostanie ukończona, komunikat zostanie już rozpropagowany do bloku.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Wskazuje blok, który powinien zostać odrzucony.|
|[initialize_source_and_target](#initialize_source_and_target)|Inicjuje obiekt podstawowy. W tym celu należy zainicjować obiekt `message_processor`.|
|[link_source](#link_source)|Łączy określony blok źródłowy z tym obiektem `propagator_block`.|
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Jest to przydatne tylko w przypadku bloków propagator, które pochodzą z source_block (zastąpień [source_block::p rocess_input_messages](source-block-class.md#process_input_messages)).|
|[propagate_message](#propagate_message)|Gdy jest zastępowany w klasie pochodnej, Metoda ta asynchronicznie przekazuje komunikat z bloku `ISource` do tego obiektu `propagator_block`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[register_filter](#register_filter)|Rejestruje metodę filtru, która będzie wywoływana dla każdej otrzymanej wiadomości.|
|[remove_network_links](#remove_network_links)|Usuwa wszystkie źródłowe i docelowe linki sieciowe z tego obiektu `propagator_block`.|
|[send_message](#send_message)|Gdy jest zastępowany w klasie pochodnej, Metoda synchronicznie przekazuje komunikat z bloku `ISource` do tego obiektu `propagator_block`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|
|[unlink_source](#unlink_source)|Odłącza określony blok źródłowy od tego obiektu `propagator_block`.|
|[unlink_sources](#unlink_sources)|Odłącza wszystkie bloki źródłowe z tego obiektu `propagator_block`. (Przesłania [ITarget:: unlink_sources](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Uwagi

Aby uniknąć wielokrotnego dziedziczenia, Klasa `propagator_block` dziedziczy z klasy `source_block` i `ITarget` klasy abstrakcyjnej. Większość funkcji w klasie `target_block` jest replikowana tutaj.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Wskazuje blok, który powinien zostać odrzucony.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez destruktor, aby upewnić się, że nowe komunikaty są odrzucane, gdy zniszczenie jest w toku.

## <a name="initialize_source_and_target"></a>initialize_source_and_target

Inicjuje obiekt podstawowy. W tym celu należy zainicjować obiekt `message_processor`.

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Harmonogram, który ma być używany na potrzeby planowania zadań.

*_PScheduleGroup*<br/>
Grupa harmonogramu, która ma być używana na potrzeby planowania zadań.

## <a name="link_source"></a>link_source

Łączy określony blok źródłowy z tym obiektem `propagator_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do bloku `ISource`, który ma być połączony.

## <a name="process_input_messages"></a>process_input_messages

Przetwarzanie komunikatów wejściowych. Jest to przydatne tylko w przypadku bloków propagator, które pochodzą z source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, która ma zostać przetworzona.

## <a name="propagate"></a>rozpowszechni

Asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Metoda `propagate` jest wywoływana w bloku docelowym przez połączony blok źródłowy. Kolejkuje zadanie asynchroniczne, aby obsłużyć komunikat, jeśli nie został jeszcze umieszczony w kolejce lub wykonane.

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PMessage` lub `_PSource` jest `NULL`.

## <a name="propagate_message"></a>propagate_message

Gdy jest zastępowany w klasie pochodnej, Metoda ta asynchronicznie przekazuje komunikat z bloku `ISource` do tego obiektu `propagator_block`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="ctor"></a>propagator_block

Konstruuje obiekt `propagator_block`.

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

Niszczy obiekt `propagator_block`.

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

Rejestruje metodę filtru, która będzie wywoływana dla każdej otrzymanej wiadomości.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Metoda filtru.

## <a name="remove_network_links"></a>remove_network_links

Usuwa wszystkie źródłowe i docelowe linki sieciowe z tego obiektu `propagator_block`.

```cpp
void remove_network_links();
```

## <a name="send"></a>Wyślij

Synchronicznie inicjuje komunikat do tego bloku. Wywoływane przez blok `ISource`. Gdy ta funkcja zostanie ukończona, komunikat zostanie już rozpropagowany do bloku.

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Ta metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PMessage` lub `_PSource` jest `NULL`.

## <a name="send_message"></a>send_message

Gdy jest zastępowany w klasie pochodnej, Metoda synchronicznie przekazuje komunikat z bloku `ISource` do tego obiektu `propagator_block`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Domyślnie ten blok zwraca `declined`, chyba że jest zastępowany przez klasę pochodną.

## <a name="unlink_source"></a>unlink_source

Odłącza określony blok źródłowy od tego obiektu `propagator_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do bloku `ISource`, który ma zostać odłączone.

## <a name="unlink_sources"></a>unlink_sources

Odłącza wszystkie bloki źródłowe z tego obiektu `propagator_block`.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[source_block, klasa](source-block-class.md)<br/>
[ITarget, klasa](itarget-class.md)
