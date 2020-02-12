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
ms.openlocfilehash: 75c7697087b8b3ad8ff15ae4d08f2b4701aaa36a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142355"
---
# <a name="transformer-class"></a>Klasa transformatora

Blok komunikatów `transformer` to Jednoelementowy, uporządkowany `propagator_block`, który może akceptować komunikaty jednego typu, i umożliwia przechowywanie nieograniczonej liczby komunikatów innego typu.

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

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Funkcja](#ctor)|Przeciążone. Tworzy blok komunikatów `transformer`.|
|[~ Transformer — destruktor](#dtor)|Niszczy blok komunikatów `transformer`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten blok komunikatów `transformer`, przekazując własność do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `transformer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `transformer`.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `transformer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Wykonuje funkcję przekształcania w komunikatach wejściowych.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `transformer`. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `transformer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

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

## <a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten blok komunikatów `transformer`, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

## <a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `transformer` i zastrzeżony przez element docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zużywanego obiektu `message`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Podobnie jak `accept`, ale jest zawsze poprzedzone wywołaniem `reserve`.

## <a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym blokiem komunikatów `transformer`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `transformer`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Wykonuje funkcję przekształcania w komunikatach wejściowych.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

## <a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `transformer`.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
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

Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `transformer`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , ponieważ blok nie odkłada proponowanych komunikatów.

## <a name="ctor"></a>Funkcja

Tworzy blok komunikatów `transformer`.

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
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `transformer`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `transformer`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `_Transform_method` to Funktor z sygnaturą `_Output (_Input const &)`, która jest wywoływana przez ten blok komunikatów `transformer` do przetwarzania komunikatów.

Typ `filter_method` to Funktor z sygnaturą `bool (_Input const &)`, która jest wywoływana przez ten blok komunikatów `transformer` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="dtor"></a>~ Transformer

Niszczy blok komunikatów `transformer`.

```cpp
~transformer();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[call, klasa](call-class.md)
