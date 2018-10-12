---
title: Klasa transformatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e5c6b9d15ef2ca456fd91dbd7829d94e33e2c0a
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162233"
---
# <a name="transformer-class"></a>Klasa transformatora

A `transformer` blok komunikatów jest docelowy pojedynczego wielu źródeł, uporządkowanych `propagator_block` który może akceptować komunikaty jednego typu i jest można przechowywać nieograniczoną liczbę komunikatów innego typu.

## <a name="syntax"></a>Składnia

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>Parametry

*_Input*<br/>
Typ ładunku komunikatów zaakceptowane przez bufor.

*_Dane wyjściowe*<br/>
Typ ładunku komunikatów przechowywane i rozprowadzane się przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[transformer](#ctor)|Przeciążone. Konstruuje `transformer` Blok obsługi wiadomości.|
|[~ transformer — destruktor](#dtor)|Niszczy `transformer` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje wiadomości, które było oferowane przez to `transformer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat, który został poprzednio oferowana przez `transformer` i zastrzeżonych przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `transformer` Blok obsługi wiadomości.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `transformer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Wykonuje funkcję transformer na komunikaty wejściowe.|
|[release_message](#release_message)|Zwalnia poprzedniej wiadomości rezerwacji. (Przesłania [source_block::release_message —](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `transformer` Blok obsługi wiadomości. (Przesłania [source_block::reserve_message —](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia działanie propagacji, po udostępnieniu rezerwacji. (Przesłania [source_block::resume_propagation —](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `transformer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [itarget::supports_anonymous_source —](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

[Itarget —](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept_message"></a> accept_message

Akceptuje wiadomości, które było oferowane przez to `transformer` Blok obsługi wiadomości, transfer praw własności do obiektu wywołującego.

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

##  <a name="consume_message"></a> consume_message

Wykorzystuje komunikat, który został poprzednio oferowana przez `transformer` i zastrzeżonych przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu są używane.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale zawsze jest poprzedzony przez wywołanie `reserve`.

##  <a name="link_target_notification"></a> link_target_notification —

Wywołanie zwrotne, które informuje, że nowy obiekt docelowy została połączona z tym `transformer` Blok obsługi wiadomości.

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `transformer` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Wykonuje funkcję transformer na komunikaty wejściowe.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

##  <a name="release_message"></a> release_message

Zwalnia poprzedniej wiadomości rezerwacji.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

##  <a name="reserve_message"></a> reserve_message

Zarezerwowaniu wiadomości przez oferowane wcześniej to `transformer` Blok obsługi wiadomości.

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

Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `transformer` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
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

##  <a name="ctor"></a> Transformer

Konstruuje `transformer` Blok obsługi wiadomości.

```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkcja, która zostanie wywołana dla każdego komunikatu akceptowane.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, do łączenia za pomocą przekształcania.

*_Filtruj*<br/>
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `transformer` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `transformer` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Typ `_Transform_method` jest funktor za pomocą podpisu `_Output (_Input const &)` który zostanie wywołany przez to `transformer` Blok obsługi wiadomości, aby przetworzyć komunikatu.

Typ `filter_method` jest funktor za pomocą podpisu `bool (_Input const &)` który zostanie wywołany przez to `transformer` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.

##  <a name="dtor"></a> ~ transformer

Niszczy `transformer` Blok obsługi wiadomości.

```
~transformer();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[call, klasa](call-class.md)
