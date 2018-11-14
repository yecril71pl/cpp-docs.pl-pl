---
title: Klasa wyboru
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 60b09b674bec58a7d35a9a37d9a8f4c40d8cd522
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522730"
---
# <a name="choice-class"></a>Klasa wyboru

A `choice` blok komunikatów jest wielu źródeł, docelowy pojedynczego bloku, który reprezentuje przepływ sterowania interakcje zestawu źródeł. Blok wyboru będzie czekać na jeden z wielu źródeł, który zwróci komunikat i rozpropaguje indeks źródła, które generowany komunikat.

## <a name="syntax"></a>Składnia

```
template<
    class T
>
class choice: public ISource<size_t>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
A `tuple`— na podstawie typ reprezentujący ładunki źródeł danych wejściowych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wybór](#ctor)|Przeciążone. Konstruuje `choice` Blok obsługi wiadomości.|
|[~ choice — destruktor](#dtor)|Niszczy `choice` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zaakceptuj](#accept)|Akceptuje wiadomości, które było oferowane przez to `choice` bloku, przenoszenia własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje licznik odwołań, w tym `choice` Blok obsługi wiadomości, aby zapobiec usunięciu.|
|[Używanie](#consume)|Wykorzystuje komunikat oferowane wcześniej to `choice` bloku komunikatów i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[has_value](#has_value)|Sprawdza, czy to `choice` Blok obsługi wiadomości został zainicjowany z wartością jeszcze.|
|[index](#index)|Zwraca indeks `tuple` reprezentujący element wybranych przez `choice` Blok obsługi wiadomości.|
|[link_target](#link_target)|Łączy to blok docelowy `choice` Blok obsługi wiadomości.|
|[Wydania](#release)|Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.|
|[release_ref](#release_ref)|Zwalnia licznik odwołań, w tym `choice` Blok obsługi wiadomości.|
|[reserve](#reserve)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `choice` Blok obsługi wiadomości.|
|[unlink_target](#unlink_target)|Wstrzymuje blok docelowy z tego `choice` Blok obsługi wiadomości.|
|[unlink_targets](#unlink_targets)|Wstrzymuje wszystkie elementy docelowe z tego `choice` Blok obsługi wiadomości. (Przesłania [isource::unlink_targets —](isource-class.md#unlink_targets).)|
|[value](#value)|Pobiera komunikat, którego indeks został wybrany przez `choice` Blok obsługi wiadomości.|

## <a name="remarks"></a>Uwagi

Blok wyboru zapewnia tylko jeden komunikaty przychodzące używane.

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

`choice`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept"></a> Zaakceptuj

Akceptuje wiadomości, które było oferowane przez to `choice` bloku, przenoszenia własności do obiektu wywołującego.

```
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `accept` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wiadomości, że obiekt wywołujący ma teraz własności.

##  <a name="acquire_ref"></a> acquire_ref —

Uzyskuje licznik odwołań, w tym `choice` Blok obsługi wiadomości, aby zapobiec usunięciu.

```
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest kojarzony z tym źródłem podczas `link_target` metody.

##  <a name="ctor"></a> Wybór

Konstruuje `choice` Blok obsługi wiadomości.

```
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>Parametry

*_Tuple*<br/>
A `tuple` źródeł wyboru tych elementów.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `choice` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `choice` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

*_Choice*<br/>
A `choice` Blok obsługi wiadomości do skopiowania. Należy pamiętać, że oryginalnego obiektu jest oddzielona, dzięki czemu to Konstruktor przenoszący.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Konstrukcja przenoszenia nie jest wykonywana w ramach blokady, co oznacza, że zależy użytkownika, aby upewnić się, lotu w czasie przenoszenia nie ma żadnych zadań lekki. W przeciwnym razie sam liczne mogą wystąpić, prowadzące do wyjątków lub niespójny stan.

##  <a name="dtor"></a> ~ Wybór

Niszczy `choice` Blok obsługi wiadomości.

```
~choice();
```

##  <a name="consume"></a> Używanie

Wykorzystuje komunikat oferowane wcześniej to `choice` bloku komunikatów i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z zarezerwowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `consume` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, że obiekt wywołujący ma teraz własności.

### <a name="remarks"></a>Uwagi

`consume` Metoda jest podobna do `accept`, ale zawsze musi być poprzedzony przez wywołanie `reserve` zwróconą **true**.

##  <a name="has_value"></a> has_value —

Sprawdza, czy to `choice` Blok obsługi wiadomości został zainicjowany z wartością jeszcze.

```
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** odebranie bloku ma wartość **false** inaczej.

##  <a name="index"></a> Indeks

Zwraca indeks `tuple` reprezentujący element wybranych przez `choice` Blok obsługi wiadomości.

```
size_t index();
```

### <a name="return-value"></a>Wartość zwracana

Indeks wiadomości.

### <a name="remarks"></a>Uwagi

Ładunek komunikatu można wyodrębnić za pomocą `get` metody.

##  <a name="link_target"></a> link_target —

Łączy to blok docelowy `choice` Blok obsługi wiadomości.

```
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku, aby połączyć to `choice` Blok obsługi wiadomości.

##  <a name="release"></a> Wydania

Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `release` metody.

##  <a name="release_ref"></a> release_ref —

Zwalnia licznik odwołań, w tym `choice` Blok obsługi wiadomości.

```
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródłowy może zwolnić wszystkie zasoby, które są zarezerwowane dla blok docelowy.

##  <a name="reserve"></a> Zarezerwuj

Zarezerwowaniu wiadomości przez oferowane wcześniej to `choice` Blok obsługi wiadomości.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `reserve` metody.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli komunikat został pomyślnie zarezerwowany, **false** inaczej. Rezerwacji może się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowane przez inny obiekt docelowy, źródła można odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu metody `reserve`, jeśli się powiedzie, należy wywołać albo `consume` lub `release` aby można było podjąć lub zrezygnować z posiadania wiadomości, odpowiednio.

##  <a name="unlink_target"></a> unlink_target —

Wstrzymuje blok docelowy z tego `choice` Blok obsługi wiadomości.

```
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku można odłączyć od to `choice` Blok obsługi wiadomości.

##  <a name="unlink_targets"></a> unlink_targets —

Wstrzymuje wszystkie elementy docelowe z tego `choice` Blok obsługi wiadomości.

```
virtual void unlink_targets();
```

### <a name="remarks"></a>Uwagi

Ta metoda nie musi być wywoływana z destruktora, ponieważ destruktor dla wewnętrznego `single_assignment` blok spowoduje to odłączenie prawidłowo.

##  <a name="value"></a> Wartość

Pobiera komunikat, którego indeks został wybrany przez `choice` Blok obsługi wiadomości.

```
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Parametry

*_Payload_type*<br/>
Typ ładunek komunikatu.

### <a name="return-value"></a>Wartość zwracana

Obciążenie komunikatu.

### <a name="remarks"></a>Uwagi

Ponieważ `choice` Blok obsługi wiadomości można pobrać dane wejściowe z ładunku różnych typów, należy określić typ ładunku punkcie pobierania. Można określić typ bazując na wynik `index` metody.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[join, klasa](join-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
