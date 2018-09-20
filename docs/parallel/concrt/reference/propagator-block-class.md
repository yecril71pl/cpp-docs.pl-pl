---
title: propagator_block — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94fd117f43dac30aef33bef9e085f5f2fcd9d2f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376542"
---
# <a name="propagatorblock-class"></a>propagator_block — Klasa

`propagator_block` Klasa jest abstrakcyjna klasa bazowa dla bloków komunikatów, które są zarówno źródłowy, jak i obiektem docelowym. Łączy ona funkcje zarówno `source_block` i `target_block` klasy.

## <a name="syntax"></a>Składnia

```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Link rejestru, który ma być używany do przechowywania łącza miejsc docelowych.

*_SourceLinkRegistry*<br/>
Link rejestru, który ma być używany do przechowywania linków źródła.

*_MessageProcessorType*<br/>
Typ procesora do przetwarzania komunikatów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`source_iterator`|Typ iteratora dla `source_link_manager` tego `propagator_block`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[propagator_block](#ctor)|Konstruuje `propagator_block` obiektu.|
|[~propagator_block Destructor](#dtor)|Niszczy `propagator_block` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[propagate](#propagate)|Asynchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.|
|[Wyślij](#send)|Inicjuje synchronicznie wiadomość do tego bloku. Wywoływane przez `ISource` bloku. Po zakończeniu działania tej funkcji, komunikat już mieć propagowane do bloku.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Wskazuje, jak blok nowe komunikaty powinny być odrzucone.|
|[initialize_source_and_target](#initialize_source_and_target)|Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.|
|[link_source](#link_source)|Łączy to blok określone źródło `propagator_block` obiektu.|
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla propagator bloków, które wynikają z source_block (zastępuje [source_block::process_input_messages —](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `propagator_block` obiektu. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[register_filter](#register_filter)|Rejestruje filter — metoda, która zostanie wywołana na każdego odebranego komunikatu.|
|[remove_network_links](#remove_network_links)|Usuwa wszystkie źródłowa i docelowa sieć łącza z tego `propagator_block` obiektu.|
|[send_message](#send_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznego komunikatu z `ISource` bloku, aby to `propagator_block` obiektu. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[unlink_source](#unlink_source)|Wstrzymuje bloku określonego źródła, z tego `propagator_block` obiektu.|
|[unlink_sources](#unlink_sources)|Odłączenie wszystkich bloków źródła z tego `propagator_block` obiektu. (Przesłania [itarget::unlink_sources —](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Uwagi

Aby uniknąć wielokrotnego dziedziczenia `propagator_block` klasa dziedziczy `source_block` klasy i `ITarget` klasy abstrakcyjnej. Większość funkcji w `target_block` klasy są replikowane w tym miejscu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[Itarget —](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="decline_incoming_messages"></a> decline_incoming_messages —

Wskazuje, jak blok nowe komunikaty powinny być odrzucone.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez destruktora, aby upewnić się, w trakcie niszczenia odrzucane nowych wiadomości.

##  <a name="initialize_source_and_target"></a> initialize_source_and_target —

Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.

```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Harmonogram, który ma być używany w przypadku planowania zadań.

*_PScheduleGroup*<br/>
Grupy harmonogramu, który ma być używany w przypadku planowania zadań.

##  <a name="link_source"></a> link_source

Łączy to blok określone źródło `propagator_block` obiektu.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do `ISource` blok, który ma być połączony.

##  <a name="process_input_messages"></a> process_input_messages —

Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla propagator bloków, które wynikają z source_block

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być przetwarzane.

##  <a name="propagate"></a> Propagacja

Asynchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.

```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

`propagate` Metoda jest wywoływana w bloku docelowego za pomocą bloku połączone źródło. Jego umieszcza w kolejce zadanie asynchroniczne, by obsłużyć komunikat, jeśli nie jest już Zakolejkowane lub wykonywania.

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

##  <a name="propagate_message"></a> propagate_message

W przypadku przesłonięcia w klasie pochodnej, ta metoda asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `propagator_block` obiektu. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="ctor"></a> propagator_block —

Konstruuje `propagator_block` obiektu.

```
propagator_block();
```

##  <a name="dtor"></a> ~ propagator_block

Niszczy `propagator_block` obiektu.

```
virtual ~propagator_block();
```

##  <a name="register_filter"></a> register_filter —

Rejestruje filter — metoda, która zostanie wywołana na każdego odebranego komunikatu.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filtruj*<br/>
Metoda filtru.

##  <a name="remove_network_links"></a> remove_network_links —

Usuwa wszystkie źródłowa i docelowa sieć łącza z tego `propagator_block` obiektu.

```
void remove_network_links();
```

##  <a name="send"></a> Wyślij

Inicjuje synchronicznie wiadomość do tego bloku. Wywoływane przez `ISource` bloku. Po zakończeniu działania tej funkcji, komunikat już mieć propagowane do bloku.

```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

Ta metoda wyrzuca [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

##  <a name="send_message"></a> send_message

W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznego komunikatu z `ISource` bloku, aby to `propagator_block` obiektu. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

Domyślnie, zwraca ten blok `declined` Jeśli zastąpiona przez klasę pochodną.

##  <a name="unlink_source"></a> unlink_source

Wstrzymuje bloku określonego źródła, z tego `propagator_block` obiektu.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do `ISource` blok, który ma być odłączone.

##  <a name="unlink_sources"></a> unlink_sources

Odłączenie wszystkich bloków źródła z tego `propagator_block` obiektu.

```
virtual void unlink_sources();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[source_block, klasa](source-block-class.md)<br/>
[ITarget, klasa](itarget-class.md)
