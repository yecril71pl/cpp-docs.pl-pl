---
title: source_block — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f5b84020d9428066bdadfff53500d671233f07d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386733"
---
# <a name="sourceblock-class"></a>source_block — Klasa

`source_block` Klasa jest abstrakcyjna klasa bazowa dla bloków tylko do źródła. Klasa oferuje łącze podstawowe funkcje zarządzania jako również jako common sprawdzanie błędów.

## <a name="syntax"></a>Składnia

```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

#### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Rejestr Link służący do przechowywania łącza miejsc docelowych.

*_MessageProcessorType*<br/>
Typ procesora do przetwarzania komunikatów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`target_iterator`|Iterator, aby zapoznać się z połączonych obiektów docelowych.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[source_block](#ctor)|Konstruuje `source_block` obiektu.|
|[~ source_block — destruktor](#dtor)|Niszczy `source_block` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zaakceptuj](#accept)|Akceptuje wiadomości, które było oferowane przez to `source_block` obiektu, przenoszenia własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje licznik odwołań, w tym `source_block` obiektu, aby zapobiec usunięciu.|
|[Używanie](#consume)|Wykorzystuje komunikat oferowane wcześniej to `source_block` obiektu i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target](#link_target)|Łączy to blok docelowy `source_block` obiektu.|
|[Wydania](#release)|Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.|
|[release_ref](#release_ref)|Zwalnia licznik odwołań, w tym `source_block` obiektu.|
|[reserve](#reserve)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `source_block` obiektu.|
|[unlink_target](#unlink_target)|Wstrzymuje blok docelowy z tego `source_block` obiektu.|
|[unlink_targets](#unlink_targets)|Odłączenie wszystkich bloków docelowych z tego `source_block` obiektu. (Przesłania [isource::unlink_targets —](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|W przypadku przesłonięcia w klasie pochodnej, akceptuje komunikat oferowane przez źródło. Bloki komunikatów powinny przesłaniać tę metodę, aby sprawdzić poprawność `_MsgId` i zwrócić komunikat.|
|[async_send](#async_send)|Asynchronicznie ustawia w kolejce komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to zrobione już|
|[consume_message](#consume_message)|W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat, który wcześniej został zarezerwowany.|
|[enable_batched_processing](#enable_batched_processing)|Umożliwia wsadowe przetwarzanie dla tego bloku.|
|[initialize_source](#initialize_source)|Inicjuje `message_propagator` w ramach tej `source_block`.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `source_block` obiektu.|
|[process_input_messages](#process_input_messages)|Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla propagator bloków, które wynikają z source_block|
|[propagate_output_messages](#propagate_output_messages)|Propagacja komunikatów do celów.|
|[propagate_to_any_targets](#propagate_to_any_targets)|W przypadku przesłonięcia w klasie pochodnej, propaguje tego komunikatu do jednej lub wszystkich połączonych elementów docelowych. Jest to procedura propagacji głównych bloków komunikatów.|
|[release_message](#release_message)|W przypadku przesłonięcia w klasie pochodnej, zwalnia poprzedniej wiadomości rezerwacji.|
|[remove_targets —](#remove_targets)|Usuwa wszystkie łącza miejsc docelowych dla tego bloku źródła. Powinna to być wywoływana z destruktora.|
|[reserve_message](#reserve_message)|W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat oferowane wcześniej to `source_block` obiektu.|
|[resume_propagation](#resume_propagation)|W przypadku przesłonięcia w klasie pochodnej, wznawia propagacji po udostępnieniu rezerwacji.|
|[sync_send](#sync_send)|Synchronicznie kolejki komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to zrobione już.|
|[unlink_target_notification](#unlink_target_notification)|Wywołanie zwrotne, które informuje, czy element docelowy zostały odłączone od tego `source_block` obiektu.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Czeka, aż wszystkie asynchronicznego propagacji zakończyć. Ten oczekiwania pokrętła specyficzne dla propagator umożliwia w destruktorach bloki komunikatów upewnij się, że wszystkie propagacji asynchronicznego czasu na zakończenie przed niszczenie bloku.|

## <a name="remarks"></a>Uwagi

Bloki komunikatów powinien pochodzić z tego bloku, aby skorzystać z łącza zarządzania i synchronizacji, dostarczone przez tę klasę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

`source_block`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept"></a> Zaakceptuj

Akceptuje wiadomości, które było oferowane przez to `source_block` obiektu, przenoszenia własności do obiektu wywołującego.

```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `accept` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

`accept` Metoda jest wywoływana przez obiekt docelowy, gdy komunikat jest oferowana przez to `ISource` bloku. Zwrócony wskaźnik komunikat może być inny niż ten, który został przekazany do `propagate` metody `ITarget` zablokować, jeśli to źródło zdecyduje się na kopię wiadomości.

##  <a name="accept_message"></a> accept_message

W przypadku przesłonięcia w klasie pochodnej, akceptuje komunikat oferowane przez źródło. Bloki komunikatów powinny przesłaniać tę metodę, aby sprawdzić poprawność `_MsgId` i zwrócić komunikat.

```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Tożsamość obiektu środowisko uruchomieniowe `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wiadomości, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Aby przenieść własność, oryginalny wskaźnik wiadomość ma zostać zwrócony. Aby zachować prawo własności, kopię ładunek komunikatu musi zostać wykonane i zwrócony.

##  <a name="acquire_ref"></a> acquire_ref —

Uzyskuje licznik odwołań, w tym `source_block` obiektu, aby zapobiec usunięciu.

```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest kojarzony z tym źródłem podczas `link_target` metody.

##  <a name="async_send"></a> async_send —

Asynchronicznie ustawia w kolejce komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to zrobione już

```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do `message` obiekt do asynchronicznego wysyłania.

##  <a name="consume"></a> Używanie

Wykorzystuje komunikat oferowane wcześniej to `source_block` obiektu i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z zarezerwowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `consume` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

Metoda zgłasza [bad_target —](bad-target-class.md) wyjątek Jeśli parametr `_PTarget` nie reprezentuje element docelowy o nazwie `reserve`.

`consume` Metoda jest podobna do `accept`, ale zawsze musi być poprzedzony przez wywołanie `reserve` zwróconą `true`.

##  <a name="consume_message"></a> consume_message

W przypadku przesłonięcia w klasie pochodnej, zużywa komunikat, który wcześniej został zarezerwowany.

```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu są używane.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wiadomości, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.

##  <a name="enable_batched_processing"></a> enable_batched_processing —

Umożliwia wsadowe przetwarzanie dla tego bloku.

```
void enable_batched_processing();
```

##  <a name="initialize_source"></a> initialize_source —

Inicjuje `message_propagator` w ramach tej `source_block`.

```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Harmonogram, który ma być używany w przypadku planowania zadań.

*_PScheduleGroup*<br/>
Grupy harmonogramu, który ma być używany w przypadku planowania zadań.

##  <a name="link_target"></a> link_target —

Łączy to blok docelowy `source_block` obiektu.

```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku, aby połączyć to `source_block` obiektu.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `source_block` obiektu.

```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

##  <a name="process_input_messages"></a> process_input_messages —

Przetwarzanie komunikatów wejściowych. Ta opcja jest przydatna dla propagator bloków, które wynikają z source_block

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być przetwarzane.

##  <a name="propagate_output_messages"></a> propagate_output_messages —

Propagacja komunikatów do celów.

```
virtual void propagate_output_messages();
```

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

W przypadku przesłonięcia w klasie pochodnej, propaguje tego komunikatu do jednej lub wszystkich połączonych elementów docelowych. Jest to procedura propagacji głównych bloków komunikatów.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik na komunikat, który ma być propagowane.

##  <a name="release"></a> Wydania

Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z zarezerwowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `release` metody.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

Metoda zgłasza [bad_target —](bad-target-class.md) wyjątek Jeśli parametr `_PTarget` nie reprezentuje element docelowy o nazwie `reserve`.

##  <a name="release_message"></a> release_message

W przypadku przesłonięcia w klasie pochodnej, zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="release_ref"></a> release_ref —

Zwalnia licznik odwołań, w tym `source_block` obiektu.

```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródłowy może zwolnić wszystkie zasoby, które są zarezerwowane dla blok docelowy.

##  <a name="remove_targets"></a> remove_targets —

Usuwa wszystkie łącza miejsc docelowych dla tego bloku źródła. Powinna to być wywoływana z destruktora.

```
void remove_targets();
```

##  <a name="reserve"></a> Zarezerwuj

Zarezerwowaniu wiadomości przez oferowane wcześniej to `source_block` obiektu.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `reserve` metody.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Rezerwacji może się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowane przez inny obiekt docelowy, źródła można odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

Po wywołaniu metody `reserve`, jeśli się powiedzie, należy wywołać albo `consume` lub `release` aby można było podjąć lub zrezygnować z posiadania wiadomości, odpowiednio.

##  <a name="reserve_message"></a> reserve_message

W przypadku przesłonięcia w klasie pochodnej, rezerwuje komunikat oferowane wcześniej to `source_block` obiektu.

```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej.

### <a name="remarks"></a>Uwagi

Po `reserve` jest wywoływana, jeśli zwróci ona `true`, albo `consume` lub `release` musi zostać wywołana wersji własności wiadomości lub wykonać.

##  <a name="resume_propagation"></a> resume_propagation

W przypadku przesłonięcia w klasie pochodnej, wznawia propagacji po udostępnieniu rezerwacji.

```
virtual void resume_propagation() = 0;
```

##  <a name="ctor"></a> source_block —

Konstruuje `source_block` obiektu.

```
source_block();
```

##  <a name="dtor"></a> ~ source_block

Niszczy `source_block` obiektu.

```
virtual ~source_block();
```

##  <a name="sync_send"></a> sync_send —

Synchronicznie kolejki komunikaty i uruchamia zadanie propagacji, jeśli nie zostało to zrobione już.

```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Wskaźnik do `message` obiekt do wysyłania synchronicznie.

##  <a name="unlink_target"></a> unlink_target —

Wstrzymuje blok docelowy z tego `source_block` obiektu.

```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku można odłączyć od to `source_block` obiektu.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek Jeśli parametr `_PTarget` jest `NULL`.

##  <a name="unlink_target_notification"></a> unlink_target_notification

Wywołanie zwrotne, które informuje, czy element docelowy zostały odłączone od tego `source_block` obiektu.

```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
`ITarget` Blok, który zostało odłączone.

##  <a name="unlink_targets"></a> unlink_targets —

Odłączenie wszystkich bloków docelowych z tego `source_block` obiektu.

```
virtual void unlink_targets();
```

##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends —

Czeka, aż wszystkie asynchronicznego propagacji zakończyć. Ten oczekiwania pokrętła specyficzne dla propagator umożliwia w destruktorach bloki komunikatów upewnij się, że wszystkie propagacji asynchronicznego czasu na zakończenie przed niszczenie bloku.

```
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ISource, klasa](isource-class.md)
