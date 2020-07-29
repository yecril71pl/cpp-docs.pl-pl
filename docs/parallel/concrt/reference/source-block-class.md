---
title: source_block — Klasa
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 304bc65d969fa677d67bf578021a63f628e0a1f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228443"
---
# <a name="source_block-class"></a>source_block — Klasa

`source_block`Klasa jest abstrakcyjną klasą bazową dla bloków przeznaczonych tylko do źródła. Klasa zawiera podstawowe funkcje zarządzania łączami oraz typowe kontrole błędów.

## <a name="syntax"></a>Składnia

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Połącz rejestr, który ma być używany do przechowywania linków docelowych.

*_MessageProcessorType*<br/>
Typ procesora do przetwarzania komunikatów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`target_iterator`|Iterator, aby przeprowadzić połączone obiekty docelowe.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[source_block](#ctor)|Konstruuje `source_block` obiekt.|
|[~ source_block destruktor](#dtor)|Niszczy `source_block` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[odebrać](#accept)|Akceptuje komunikat oferowany przez ten `source_block` obiekt, przekazując własność do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje liczbę odwołań dla tego `source_block` obiektu, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Wykorzystuje komunikat wcześniej oferowany przez ten `source_block` obiekt i został pomyślnie zarezerwowany przez element docelowy, przez przeniesienie własności do obiektu wywołującego.|
|[link_target](#link_target)|Łączy blok docelowy z tym `source_block` obiektem.|
|[Usuwanie](#release)|Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.|
|[release_ref](#release_ref)|Zwalnia liczbę odwołań dla tego `source_block` obiektu.|
|[zarezerwować](#reserve)|Rezerwuje komunikat wcześniej oferowany przez ten `source_block` obiekt.|
|[unlink_target](#unlink_target)|Odłącza blok docelowy od tego `source_block` obiektu.|
|[unlink_targets](#unlink_targets)|Odłącza wszystkie bloki docelowe z tego `source_block` obiektu. (Przesłania [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Gdy jest zastępowany w klasie pochodnej, akceptuje oferowany komunikat przez źródło. Bloki komunikatów powinny zastąpić tę metodę, aby zweryfikować `_MsgId` i zwrócić komunikat.|
|[async_send](#async_send)|Asynchronicznie kolejkuje komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to jeszcze zrobione|
|[consume_message](#consume_message)|Gdy jest zastępowany w klasie pochodnej, wykorzystuje wcześniej zarezerwowany komunikat.|
|[enable_batched_processing](#enable_batched_processing)|Włącza przetwarzanie wsadowe dla tego bloku.|
|[initialize_source](#initialize_source)|Inicjuje w `message_propagator` tym elemencie `source_block` .|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `source_block` obiektem.|
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Jest to przydatne tylko w przypadku bloków propagator, które pochodzą z source_block|
|[propagate_output_messages](#propagate_output_messages)|Propagowanie komunikatów do obiektów docelowych.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Gdy jest zastępowany w klasie pochodnej, propaguje dany komunikat do dowolnych lub wszystkich połączonych obiektów docelowych. Jest to główna procedura propagacji dla bloków komunikatów.|
|[release_message](#release_message)|Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednią rezerwację wiadomości.|
|[remove_targets](#remove_targets)|Usuwa wszystkie linki docelowe dla tego bloku źródłowego. Ta wartość powinna być wywoływana z destruktora.|
|[reserve_message](#reserve_message)|Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten `source_block` obiekt.|
|[resume_propagation](#resume_propagation)|Gdy jest zastępowany w klasie pochodnej, wznawia propagowanie po wydaniu rezerwacji.|
|[sync_send](#sync_send)|Synchronicznie kolejkuje komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to jeszcze zrobione.|
|[unlink_target_notification](#unlink_target_notification)|Wywołanie zwrotne, które powiadamia, że element docelowy został odłączone od tego `source_block` obiektu.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Czeka na zakończenie wszystkich propagacji asynchronicznych. Ten odczekanie dla tego obiektu jest używany w destruktorach bloków komunikatów, aby upewnić się, że wszystkie propagacje asynchroniczne mają czas do zakończenia przed zniszczeniem bloku.|

## <a name="remarks"></a>Uwagi

Bloki komunikatów powinny pochodzić od tego bloku, aby skorzystać z funkcji zarządzania linkami i synchronizacji dostarczonych przez tę klasę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a><a name="accept"></a>odebrać

Akceptuje komunikat oferowany przez ten `source_block` obiekt, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `accept` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

`accept`Metoda jest wywoływana przez obiekt docelowy, podczas gdy komunikat jest oferowany przez ten `ISource` blok. Zwrócony wskaźnik komunikatu może być inny niż przekazana do `propagate` metody `ITarget` bloku, jeśli to źródło zdecyduje się wykonać kopię wiadomości.

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Gdy jest zastępowany w klasie pochodnej, akceptuje oferowany komunikat przez źródło. Bloki komunikatów powinny zastąpić tę metodę, aby zweryfikować `_MsgId` i zwrócić komunikat.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Tożsamość obiektu środowiska uruchomieniowego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Aby przenieść własność, należy zwrócić oryginalny wskaźnik wiadomości. Aby zachować własność, należy wprowadzić i zwrócić kopię ładunku komunikatów.

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

Uzyskuje liczbę odwołań dla tego `source_block` obiektu, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączony z tym źródłem podczas tej `link_target` metody.

## <a name="async_send"></a><a name="async_send"></a>async_send

Asynchronicznie kolejkuje komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to jeszcze zrobione

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do `message` obiektu, który asynchronicznie wysyła.

## <a name="consume"></a><a name="consume"></a>wykorzystania

Wykorzystuje komunikat wcześniej oferowany przez ten `source_block` obiekt i został pomyślnie zarezerwowany przez element docelowy, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity`Obiekt zastrzeżony `message` .

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `consume` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

Metoda zgłasza wyjątek [bad_target](bad-target-class.md) , jeśli parametr nie `_PTarget` reprezentuje obiektu docelowego, który został wywołany `reserve` .

`consume`Metoda jest podobna do `accept` , ale musi być zawsze poprzedzona wywołaniem `reserve` zwracanym **`true`** .

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Gdy jest zastępowany w klasie pochodnej, wykorzystuje wcześniej zarezerwowany komunikat.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Używany obiekt.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Przypomina `accept` , ale jest zawsze poprzedzone wywołaniem do `reserve` .

## <a name="enable_batched_processing"></a><a name="enable_batched_processing"></a>enable_batched_processing

Włącza przetwarzanie wsadowe dla tego bloku.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a><a name="initialize_source"></a>initialize_source

Inicjuje w `message_propagator` tym elemencie `source_block` .

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Harmonogram, który ma być używany na potrzeby planowania zadań.

*_PScheduleGroup*<br/>
Grupa harmonogramu, która ma być używana na potrzeby planowania zadań.

## <a name="link_target"></a><a name="link_target"></a>link_target

Łączy blok docelowy z tym `source_block` obiektem.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku, `ITarget` który ma zostać połączony z tym `source_block` obiektem.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `source_block` obiektem.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

Przetwarzanie komunikatów wejściowych. Jest to przydatne tylko w przypadku bloków propagator, które pochodzą z source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, która ma zostać przetworzona.

## <a name="propagate_output_messages"></a><a name="propagate_output_messages"></a>propagate_output_messages

Propagowanie komunikatów do obiektów docelowych.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Gdy jest zastępowany w klasie pochodnej, propaguje dany komunikat do dowolnych lub wszystkich połączonych obiektów docelowych. Jest to główna procedura propagacji dla bloków komunikatów.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do komunikatu, który ma być propagowany.

## <a name="release"></a><a name="release"></a>Usuwanie

Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity`Obiekt zastrzeżony `message` .

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `release` metodę.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

Metoda zgłasza wyjątek [bad_target](bad-target-class.md) , jeśli parametr nie `_PTarget` reprezentuje obiektu docelowego, który został wywołany `reserve` .

## <a name="release_message"></a><a name="release_message"></a>release_message

Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

Zwalnia liczbę odwołań dla tego `source_block` obiektu.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="remove_targets"></a><a name="remove_targets"></a>remove_targets

Usuwa wszystkie linki docelowe dla tego bloku źródłowego. Ta wartość powinna być wywoływana z destruktora.

```cpp
void remove_targets();
```

## <a name="reserve"></a><a name="reserve"></a>zarezerwować

Rezerwuje komunikat wcześniej oferowany przez ten `source_block` obiekt.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `reserve` metodę.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie. Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

Po wywołaniu `reserve` , jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu przeprowadzenia lub zadawać swój komunikat odpowiednio.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten `source_block` obiekt.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Obiekt, który jest `runtime_object_identity` `message` zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Po `reserve` wywołaniu, jeśli zwróci **`true`** , `consume` lub `release` musi zostać wywołana w celu podjęcia lub zwolnienia własności wiadomości.

## <a name="resume_propagation"></a><a name="resume_propagation"></a>resume_propagation

Gdy jest zastępowany w klasie pochodnej, wznawia propagowanie po wydaniu rezerwacji.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="source_block"></a><a name="ctor"></a>source_block

Konstruuje `source_block` obiekt.

```cpp
source_block();
```

## <a name="source_block"></a><a name="dtor"></a>~ source_block

Niszczy `source_block` obiekt.

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a><a name="sync_send"></a>sync_send

Synchronicznie kolejkuje komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to jeszcze zrobione.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do `message` obiektu do synchronicznego wysłania.

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

Odłącza blok docelowy od tego `source_block` obiektu.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku, `ITarget` Aby odłączyć od tego `source_block` obiektu.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PTarget` ma wartość `NULL` .

## <a name="unlink_target_notification"></a><a name="unlink_target_notification"></a>unlink_target_notification

Wywołanie zwrotne, które powiadamia, że element docelowy został odłączone od tego `source_block` obiektu.

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
`ITarget`Blok, który został odłączone.

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

Odłącza wszystkie bloki docelowe z tego `source_block` obiektu.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a><a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

Czeka na zakończenie wszystkich propagacji asynchronicznych. Ten odczekanie dla tego obiektu jest używany w destruktorach bloków komunikatów, aby upewnić się, że wszystkie propagacje asynchroniczne mają czas do zakończenia przed zniszczeniem bloku.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa ISource](isource-class.md)
