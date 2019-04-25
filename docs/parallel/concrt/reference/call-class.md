---
title: Klasa wywołania
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: 9651a74fdb07ad96d6f01edb6818ea48d697c37c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337911"
---
# <a name="call-class"></a>Klasa wywołania

A `call` blok komunikatów jest wielu źródeł, uporządkowane `target_block` wywołującej określonej funkcji podczas odbierania komunikatu.

## <a name="syntax"></a>Składnia

```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów propagowane do tego bloku.

*_FunctorType*<br/>
Podpis funkcji, które akceptują tego bloku.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wywołania](#ctor)|Przeciążone. Konstruuje `call` Blok obsługi wiadomości.|
|[~ call — destruktor](#dtor)|Niszczy `call` Blok obsługi wiadomości.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Wykonuje wywołanie funkcji na komunikaty wejściowe.|
|[process_message](#process_message)|Przetwarza komunikat, który został zaakceptowany przez to `call` Blok obsługi wiadomości.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `call` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `call` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty oferowane przez źródło, który nie jest połączony. (Przesłania [itarget::supports_anonymous_source —](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Itarget —](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="ctor"></a> Wywołania

Konstruuje `call` Blok obsługi wiadomości.

```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkcja, która zostanie wywołana dla każdego komunikatu akceptowane.

*_Filter*<br/>
Funkcja filtrowania, określający, czy powinna być akceptowana oferowane wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `call` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `call` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Typ `_Call_method` jest funktor za pomocą podpisu `void (T const &)` który zostanie wywołany przez to `call` Blok obsługi wiadomości, aby przetworzyć komunikatu.

Typ `filter_method` jest funktor za pomocą podpisu `bool (T const &)` który zostanie wywołany przez to `call` Blok obsługi wiadomości, aby ustalić, czy nie powinien akceptować wiadomości oferowane.

##  <a name="dtor"></a> ~ wywołania

Niszczy `call` Blok obsługi wiadomości.

```
~call();
```

##  <a name="process_input_messages"></a> process_input_messages —

Wykonuje wywołanie funkcji na komunikaty wejściowe.

```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być obsługiwane.

##  <a name="process_message"></a> process_message —

Przetwarza komunikat, który został zaakceptowany przez to `call` Blok obsługi wiadomości.

```
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do wiadomości, które mają być obsługiwane.

##  <a name="propagate_message"></a> propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku, aby to `call` Blok obsługi wiadomości. Zostanie wywołany przez `propagate` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

##  <a name="send_message"></a> send_message

Synchronicznie przekazuje komunikat z `ISource` bloku, aby to `call` Blok obsługi wiadomości. Zostanie wywołany przez `send` metody, gdy zostanie wywołana przez blok źródłowy.

```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[transformer, klasa](transformer-class.md)
