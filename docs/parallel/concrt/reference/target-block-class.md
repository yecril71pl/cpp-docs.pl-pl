---
title: target_block — Klasa
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: cb8880b66ebeef12018ef7449c9c383b99ec396c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656897"
---
# <a name="targetblock-class"></a>target_block — Klasa

`target_block` Klasa jest abstrakcyjna klasa bazowa, zapewniająca łącze podstawowe funkcje zarządzania i tylko sprawdzanie błędów dla elementu docelowego blokuje.

## <a name="syntax"></a>Składnia

```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Parametry

*_SourceLinkRegistry*<br/>
Link rejestru, który ma być używany do przechowywania linków źródła.

*_MessageProcessorType*<br/>
Typ procesora do przetwarzania komunikatów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`source_iterator`|Typ iteratora dla `source_link_manager` tego `target_block` obiektu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[target_block](#ctor)|Konstruuje `target_block` obiektu.|
|[~ target_block — destruktor](#dtor)|Niszczy `target_block` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[propagate](#propagate)|Asynchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.|
|[Wyślij](#send)|Synchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[async_send](#async_send)|Asynchronicznie wysyła komunikat do przetworzenia.|
|[decline_incoming_messages](#decline_incoming_messages)|Wskazuje, jak blok nowe komunikaty powinny być odrzucone.|
|[enable_batched_processing](#enable_batched_processing)|Umożliwia wsadowe przetwarzanie dla tego bloku.|
|[initialize_target](#initialize_target)|Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.|
|[link_source](#link_source)|Łączy to blok określone źródło `target_block` obiektu.|
|[process_input_messages](#process_input_messages)|Przetwarza wiadomości, które są odbierane jako dane wejściowe.|
|[process_message](#process_message)|W przypadku przesłonięcia w klasie pochodnej, przetwarza komunikat, który został zaakceptowany przez to `target_block` obiektu.|
|[propagate_message](#propagate_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `target_block` obiektu. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[register_filter](#register_filter)|Rejestruje filter — metoda, która zostanie wywołana na każdy komunikat.|
|[remove_sources —](#remove_sources)|Odłączenie wszystkich źródeł oczekiwania na zakończenie operacji oczekujących asynchronicznego wysyłania.|
|[send_message](#send_message)|W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznego komunikatu z `ISource` bloku, aby to `target_block` obiektu. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[sync_send](#sync_send)|Synchronicznie, Wyślij wiadomość do przetworzenia.|
|[unlink_source](#unlink_source)|Wstrzymuje bloku określonego źródła, z tego `target_block` obiektu.|
|[unlink_sources](#unlink_sources)|Odłączenie wszystkich bloków źródła z tego `target_block` obiektu. (Przesłania [itarget::unlink_sources —](itarget-class.md#unlink_sources).)|
|[wait_for_async_sends](#wait_for_async_sends)|Czeka, aż wszystkie asynchronicznego propagacji zakończyć.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Itarget —](itarget-class.md)

`target_block`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="async_send"></a> async_send —

Asynchronicznie wysyła komunikat do przetworzenia.

```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wysyłanej wiadomości.

##  <a name="decline_incoming_messages"></a> decline_incoming_messages —

Wskazuje, jak blok nowe komunikaty powinny być odrzucone.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez destruktora, aby upewnić się, w trakcie niszczenia odrzucane nowych wiadomości.

##  <a name="enable_batched_processing"></a> enable_batched_processing —

Umożliwia wsadowe przetwarzanie dla tego bloku.

```
void enable_batched_processing();
```

##  <a name="initialize_target"></a> initialize_target —

Inicjuje obiekt podstawowy. W szczególności `message_processor` obiekt musi zostać zainicjowany.

```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Harmonogram, który ma być używany w przypadku planowania zadań.

*_PScheduleGroup*<br/>
Grupy harmonogramu, który ma być używany w przypadku planowania zadań.

##  <a name="link_source"></a> link_source

Łączy to blok określone źródło `target_block` obiektu.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do `ISource` blok, który ma być połączony.

### <a name="remarks"></a>Uwagi

Ta funkcja nie należy wywoływać bezpośrednio na `target_block` obiektu. Bloki powinny być połączone ze sobą przy użyciu `link_target` metody `ISource` bloki, które będzie wywoływać `link_source` metody odpowiedniego obiektu docelowego.

##  <a name="process_input_messages"></a> process_input_messages —

Przetwarza wiadomości, które są odbierane jako dane wejściowe.

```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być przetwarzane.

##  <a name="process_message"></a> process_message —

W przypadku przesłonięcia w klasie pochodnej, przetwarza komunikat, który został zaakceptowany przez to `target_block` obiektu.

```
virtual void process_message(message<_Source_type> *);
```

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

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

##  <a name="propagate_message"></a> propagate_message

W przypadku przesłonięcia w klasie pochodnej, ta metoda asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `target_block` obiektu. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

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

##  <a name="register_filter"></a> register_filter —

Rejestruje filter — metoda, która zostanie wywołana na każdy komunikat.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filtruj*<br/>
Metoda filtru.

##  <a name="remove_sources"></a> remove_sources —

Odłączenie wszystkich źródeł oczekiwania na zakończenie operacji oczekujących asynchronicznego wysyłania.

```
void remove_sources();
```

### <a name="remarks"></a>Uwagi

Wszystkich bloków docelowych należy wywołać tej procedury można usunąć źródła w ich destruktora.

##  <a name="send"></a> Wyślij

Synchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.

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

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

Za pomocą `send` metody poza inicjowania wiadomości i propagację wiadomości w sieci jest niebezpieczny i może prowadzić do zakleszczenia.

Gdy `send` zwraca komunikat albo już zostały zaakceptowane i przesłane do bloku docelowego lub została odrzucona przez element docelowy.

##  <a name="send_message"></a> send_message

W przypadku przesłonięcia w klasie pochodnej, ta metoda przekazuje synchronicznego komunikatu z `ISource` bloku, aby to `target_block` obiektu. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

Domyślnie, zwraca ten blok `declined` Jeśli zastąpiona przez klasę pochodną.

##  <a name="sync_send"></a> sync_send —

Synchronicznie, Wyślij wiadomość do przetworzenia.

```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wysyłanej wiadomości.

##  <a name="ctor"></a> target_block —

Konstruuje `target_block` obiektu.

```
target_block();
```

##  <a name="dtor"></a> ~ target_block

Niszczy `target_block` obiektu.

```
virtual ~target_block();
```

##  <a name="unlink_source"></a> unlink_source

Wstrzymuje bloku określonego źródła, z tego `target_block` obiektu.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Wskaźnik do `ISource` blok, który ma być odłączone.

##  <a name="unlink_sources"></a> unlink_sources

Odłączenie wszystkich bloków źródła z tego `target_block` obiektu.

```
virtual void unlink_sources();
```

##  <a name="wait_for_async_sends"></a> wait_for_async_sends —

Czeka, aż wszystkie asynchronicznego propagacji zakończyć.

```
void wait_for_async_sends();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest używana przez destruktory bloku komunikatu, aby upewnić się, że wszystkie operacje asynchroniczne mieli czas na zakończenie przed niszczenie bloku.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ITarget, klasa](itarget-class.md)
