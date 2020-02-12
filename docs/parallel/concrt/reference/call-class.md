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
ms.openlocfilehash: 445e368ced9d9c8faf30351ecaeecc4e1b8a59f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142834"
---
# <a name="call-class"></a>Klasa wywołania

Blok komunikatów `call` to wiele źródeł uporządkowanych `target_block`, które wywołuje określoną funkcję podczas otrzymywania wiadomości.

## <a name="syntax"></a>Składnia

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku komunikatów propagowanych do tego bloku.

*_FunctorType*<br/>
Sygnatura funkcji, które może zaakceptować ten blok.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[połączeń](#ctor)|Przeciążone. Tworzy blok komunikatów `call`.|
|[~ Call — destruktor](#dtor)|Niszczy blok komunikatów `call`.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Wykonuje funkcję Call w komunikatach wejściowych.|
|[process_message](#process_message)|Przetwarza komunikat, który został zaakceptowany przez ten blok komunikatów `call`.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `call`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `call`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Zastępuje metodę `supports_anonymous_source`, aby wskazać, że ten blok może akceptować komunikaty, które są do niego udostępniane przez źródło, które nie jest połączone. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>połączeń

Tworzy blok komunikatów `call`.

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
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `call`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `call`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Typ `_Call_method` to Funktor z sygnaturą `void (T const &)`, która jest wywoływana przez ten blok komunikatów `call` do przetwarzania komunikatów.

Typ `filter_method` to Funktor z sygnaturą `bool (T const &)`, która jest wywoływana przez ten blok komunikatów `call` do określenia, czy powinien on akceptować oferowany komunikat.

## <a name="dtor"></a>~ Wywołanie

Niszczy blok komunikatów `call`.

```cpp
~call();
```

## <a name="process_input_messages"></a>process_input_messages

Wykonuje funkcję Call w komunikatach wejściowych.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do komunikatu, który ma zostać obsłużony.

## <a name="process_message"></a>process_message

Przetwarza komunikat, który został zaakceptowany przez ten blok komunikatów `call`.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do komunikatu, który ma zostać obsłużony.

## <a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `call`. Jest wywoływany przez metodę `propagate`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

## <a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z bloku `ISource` do tego bloku komunikatów `call`. Jest wywoływany przez metodę `send`, gdy jest wywoływana przez blok źródłowy.

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[transformer, klasa](transformer-class.md)
