---
title: Klasa overwrite_buffer
ms.date: 11/04/2016
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 7579ee4b9c650b0fe707eccb0f8c2b67a3efac14
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231692"
---
# <a name="overwrite_buffer-class"></a>Klasa overwrite_buffer

`overwrite_buffer`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania pojedynczej wiadomości w danym momencie. Nowe wiadomości zastępują wcześniej przechowywane.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku komunikatów przechowywanych i propagowanych przez bufor.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Przeciążone. Tworzy `overwrite_buffer` blok komunikatów.|
|[~ overwrite_buffer destruktor](#dtor)|Niszczy `overwrite_buffer` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[has_value](#has_value)|Sprawdza, czy ten `overwrite_buffer` blok komunikatów ma jeszcze wartość.|
|[wartościami](#value)|Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w `overwrite_buffer` bloku obsługi komunikatów.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[accept_message](#accept_message)|Akceptuje komunikat, który był oferowany przez ten `overwrite_buffer` blok komunikatów, zwracając kopię komunikatu do obiektu wywołującego.|
|[consume_message](#consume_message)|Wykorzystuje komunikat wcześniej oferowany przez `overwrite_buffer` blok komunikatów i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.|
|[link_target_notification](#link_target_notification)|Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `overwrite_buffer` blokiem obsługi komunikatów.|
|[propagate_message](#propagate_message)|Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umieszcza `message _PMessage` w tym `overwrite_buffer` bloku komunikatów i oferuje go wszystkim połączonym obiektom docelowym.|
|[release_message](#release_message)|Zwalnia poprzednią rezerwację wiadomości. (Zastępuje [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Rezerwuje komunikat wcześniej oferowany przez ten `overwrite_buffer` blok komunikatów. (Zastępuje [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Wznawia propagację po wydaniu rezerwacji. (Zastępuje [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.|
|[supports_anonymous_source](#supports_anonymous_source)|Przesłania `supports_anonymous_source` metodę w celu wskazania, że ten blok może akceptować komunikaty, które są przez nie połączone, za pomocą źródła, które nie jest połączony. (Przesłania [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Uwagi

`overwrite_buffer`Blok komunikatów propaguje kopie przechowywanego komunikatu do każdego z jego obiektów docelowych.

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept_message"></a><a name="accept_message"></a>accept_message

Akceptuje komunikat, który był oferowany przez ten `overwrite_buffer` blok komunikatów, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

`overwrite_buffer`Blok komunikatów zwraca kopie wiadomości do jej obiektów docelowych, a nie transferuje własność aktualnie przechowywanego komunikatu.

## <a name="consume_message"></a><a name="consume_message"></a>consume_message

Wykorzystuje komunikat wcześniej oferowany przez `overwrite_buffer` blok komunikatów i zarezerwowany przez obiekt docelowy, zwracając kopię komunikatu do obiektu wywołującego.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Używany obiekt.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Przypomina `accept` , ale jest zawsze poprzedzone wywołaniem do `reserve` .

## <a name="has_value"></a><a name="has_value"></a>has_value

Sprawdza, czy ten `overwrite_buffer` blok komunikatów ma jeszcze wartość.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli blok odebrał wartość, **`false`** w przeciwnym razie.

## <a name="link_target_notification"></a><a name="link_target_notification"></a>link_target_notification

Wywołanie zwrotne, które powiadamia, że nowy element docelowy został połączony z tym `overwrite_buffer` blokiem obsługi komunikatów.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do nowo połączonego obiektu docelowego.

## <a name="overwrite_buffer"></a><a name="dtor"></a>~ overwrite_buffer

Niszczy `overwrite_buffer` blok komunikatów.

```cpp
~overwrite_buffer();
```

## <a name="overwrite_buffer"></a><a name="ctor"></a>overwrite_buffer

Tworzy `overwrite_buffer` blok komunikatów.

```cpp
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkcja filtru, która określa, czy proponowane komunikaty powinny być akceptowane.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `overwrite_buffer` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `overwrite_buffer` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Typ `filter_method` to Funktor z podpisem `bool (T const &)` , który jest wywoływany przez ten `overwrite_buffer` blok komunikatów, aby określić, czy powinien on akceptować oferowany komunikat.

## <a name="propagate_message"></a><a name="propagate_message"></a>propagate_message

Asynchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi komunikatów. Jest wywoływana przez `propagate` metodę, gdy jest wywoływana przez blok źródłowy.

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

## <a name="propagate_to_any_targets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets

Umieszcza `message _PMessage` w tym `overwrite_buffer` bloku komunikatów i oferuje go wszystkim połączonym obiektom docelowym.

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu, który przebrał `overwrite_buffer` własność.

### <a name="remarks"></a>Uwagi

Ta metoda zastępuje bieżący komunikat w `overwrite_buffer` z nowo zaakceptowanym komunikatem `_PMessage` .

## <a name="send_message"></a><a name="send_message"></a>send_message

Synchronicznie przekazuje komunikat z `ISource` bloku do tego `overwrite_buffer` bloku obsługi komunikatów. Jest wywoływana przez `send` metodę, gdy jest wywoływana przez blok źródłowy.

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

## <a name="release_message"></a><a name="release_message"></a>release_message

Zwalnia poprzednią rezerwację wiadomości.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

## <a name="reserve_message"></a><a name="reserve_message"></a>reserve_message

Rezerwuje komunikat wcześniej oferowany przez ten `overwrite_buffer` blok komunikatów.

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

## <a name="value"></a><a name="value"></a>wartościami

Pobiera odwołanie do bieżącego ładunku wiadomości przechowywanej w `overwrite_buffer` bloku obsługi komunikatów.

```cpp
T value();
```

### <a name="return-value"></a>Wartość zwracana

Ładunek obecnie przechowywanego komunikatu.

### <a name="remarks"></a>Uwagi

Wartość przechowywana w `overwrite_buffer` może ulec zmianie natychmiast po powrocie tej metody. Ta metoda będzie czekać, aż zostanie wyświetlony komunikat, jeśli żaden komunikat nie jest obecnie przechowywany w `overwrite_buffer` .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa unbounded_buffer](unbounded-buffer-class.md)<br/>
[Klasa single_assignment](single-assignment-class.md)
