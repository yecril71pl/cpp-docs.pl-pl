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
ms.openlocfilehash: d3dc730e19aaadfed171816e92837ba2766883cb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213882"
---
# <a name="call-class"></a>Klasa wywołania

`call`Blok komunikatów to wiele źródeł uporządkowane, `target_block` które wywołuje określoną funkcję podczas otrzymywania wiadomości.

## <a name="syntax"></a>Składnia

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów propagowanych do tego bloku.

*_FunctorType*<br/>
Sygnatura funkcji, które może zaakceptować ten blok.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[połączeń](#ctor)|Przeciążone. Tworzy `call` blok komunikatów.|
|[~ Call — destruktor](#dtor)|Niszczy `call` blok komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Wykonuje funkcję Call w komunikatach wejściowych.|
|[process_message](#process_message)|Przetwarza komunikat, który został zaakceptowany przez ten `call` blok komunikatów.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `call` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `call` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="call"></a><a name="ctor"></a>połączeń

Tworzy `call` blok komunikatów.

```cpp
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
Funkcja, która będzie wywoływana dla każdej zaakceptowanej wiadomości.

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `call` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `call` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Typ `_Call_method` to Funktor z podpisem `void (T const &)` , który jest wywoływany przez ten `call` blok komunikatów do przetwarzania komunikatów.

Typ `filter_method` to Funktor z podpisem `bool (T const &)` , który jest wywoływany przez ten `call` blok komunikatów, aby określić, czy powinien on akceptować oferowany komunikat.

## <a name="call"></a><a name="dtor"></a>~ Wywołanie

Niszczy `call` blok komunikatów.

```cpp
~call();
```

## <a name="process_input_messages"></a><a name="process_input_messages"></a>process_input_messages

Wykonuje funkcję Call w komunikatach wejściowych.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do komunikatu, który ma zostać obsłużony.

## <a name="process_message"></a><a name="process_message"></a>process_message

Przetwarza komunikat, który został zaakceptowany przez ten `call` blok komunikatów.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do komunikatu, który ma zostać obsłużony.

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `call` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="send_message"></a><a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z `ISource` bloku do tego `call` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[transformator — Klasa](transformer-class.md)
