---
title: Klasa transformatora
ms.date: 11/04/2016
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
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: adc83ab2d8268460b3a35be44f5733c8b6fa1c43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217899"
---
# <a name="transformer-class"></a>Klasa transformatora

`transformer`Blok obsługi komunikatów to jeden obiekt docelowy, który jest uporządkowany, `propagator_block` który może akceptować komunikaty jednego typu, i umożliwia przechowywanie nieograniczonej liczby komunikatów innego typu.

## <a name="syntax"></a>Składnia

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>Parametry

*_Input*<br/>
Typ ładunku komunikatów akceptowanych przez bufor.

*_Output*<br/>
Typ ładunku komunikatów przechowywanych i rozpropagowanych przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Funkcja](#ctor)|Przeciążone. Tworzy `transformer` blok komunikatów.|
|[~ Transformer — destruktor](#dtor)|Niszczy `transformer` blok komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten `transformer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `transformer` i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `transformer` blokiem obsługi komunikatów.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Wykonuje funkcję przekształcania w komunikatach wejściowych.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten `transformer` blok komunikatów. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten `transformer` blok komunikatów, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `transformer` i zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Używany obiekt.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Przypomina `accept` , ale jest zawsze poprzedzone wywołaniem do `reserve` .

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `transformer` blokiem obsługi komunikatów.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Wykonuje funkcję przekształcania w komunikatach wejściowych.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a><a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten `transformer` blok komunikatów.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
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

Synchronicznie przekazuje komunikat z `ISource` bloku do tego `transformer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** ponieważ blok nie odkłada proponowanych komunikatów.

## <a name="transformer"></a><a name="ctor"></a>Funkcja

Tworzy `transformer` blok komunikatów.

```cpp
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
Funkcja, która będzie wywoływana dla każdej zaakceptowanej wiadomości.

*_PTarget*<br/>
Wskaźnik do bloku docelowego do powiązania z transformatorem.

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `transformer` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `transformer` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Typ `_Transform_method` to Funktor z podpisem `_Output (_Input const &)` , który jest wywoływany przez ten `transformer` blok komunikatów do przetwarzania komunikatów.

Typ `filter_method` to Funktor z podpisem `bool (_Input const &)` , który jest wywoływany przez ten `transformer` blok komunikatów, aby określić, czy powinien on akceptować oferowany komunikat.

## <a name="transformer"></a><a name="dtor"></a>~ Transformer

Niszczy `transformer` blok komunikatów.

```cpp
~transformer();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Call, Klasa](call-class.md)
