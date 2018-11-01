---
title: multitype_join — Klasa
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 2fd94ef072fcab9af076fcdfa1b5c094d77f89c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547410"
---
# <a name="multitypejoin-class"></a>multitype_join — Klasa

A `multitype_join` blok komunikatów jest wielu źródeł, docelowy pojedynczego blok komunikatów, który łączy ze sobą wiadomości o różnych typach z każdego z jego źródła i oferuje krotki połączone komunikatów do jego obiekty docelowe.

## <a name="syntax"></a>Składnia

```
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
`tuple` Typ ładunku komunikatów przyłączone i rozprowadzane przez blok.

*_Jtype*<br/>
Rodzaj elementu `join` bloku jest, albo `greedy` lub `non_greedy`

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[multitype_join](#ctor)|Przeciążone. Konstruuje `multitype_join` Blok obsługi wiadomości.|
|[~ multitype_join — destruktor](#dtor)|Niszczy `multitype_join` Blok obsługi wiadomości.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zaakceptuj](#accept)|Akceptuje wiadomości, które było oferowane przez to `multitype_join` bloku, przenoszenia własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje licznik odwołań, w tym `multitype_join` Blok obsługi wiadomości, aby zapobiec usunięciu.|
|[Używanie](#consume)|Wykorzystuje komunikat, który został poprzednio oferowana przez `multitype_join` bloku komunikatów i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.|
|[link_target](#link_target)|Łączy to blok docelowy `multitype_join` Blok obsługi wiadomości.|
|[Wydania](#release)|Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.|
|[release_ref](#release_ref)|Zwalnia licznik odwołań, w tym `multiple_join` Blok obsługi wiadomości.|
|[reserve](#reserve)|Zarezerwowaniu wiadomości przez oferowane wcześniej to `multitype_join` Blok obsługi wiadomości.|
|[unlink_target](#unlink_target)|Wstrzymuje blok docelowy z tego `multitype_join` Blok obsługi wiadomości.|
|[unlink_targets](#unlink_targets)|Wstrzymuje wszystkie elementy docelowe z tego `multitype_join` Blok obsługi wiadomości. (Przesłania [isource::unlink_targets —](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Isource —](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="accept"></a> Zaakceptuj

Akceptuje wiadomości, które było oferowane przez to `multitype_join` bloku, przenoszenia własności do obiektu wywołującego.

```
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z oferowane `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `accept` metody.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wiadomości, że obiekt wywołujący ma teraz własności.

##  <a name="acquire_ref"></a> acquire_ref —

Uzyskuje licznik odwołań, w tym `multitype_join` Blok obsługi wiadomości, aby zapobiec usunięciu.

```
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest kojarzony z tym źródłem podczas `link_target` metody.

##  <a name="consume"></a> Używanie

Wykorzystuje komunikat, który został poprzednio oferowana przez `multitype_join` bloku komunikatów i pomyślnie zarezerwowany przez element docelowy przenoszenia własności do obiektu wywołującego.

```
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

##  <a name="link_target"></a> link_target —

Łączy to blok docelowy `multitype_join` Blok obsługi wiadomości.

```
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku, aby połączyć to `multitype_join` Blok obsługi wiadomości.

##  <a name="ctor"></a> multitype_join

Konstruuje `multitype_join` Blok obsługi wiadomości.

```
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>Parametry

*_Tuple*<br/>
A `tuple` źródeł, w tym `multitype_join` Blok obsługi wiadomości.

*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości.

*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.

*_Połącz*<br/>
A `multitype_join` Blok obsługi wiadomości do skopiowania. Należy pamiętać, że oryginalnego obiektu jest oddzielona, dzięki czemu to Konstruktor przenoszący.

### <a name="remarks"></a>Uwagi

Środowisko wykonawcze używa domyślnego harmonogramu, jeśli nie określisz `_PScheduler` lub `_PScheduleGroup` parametrów.

Konstrukcja przenoszenia nie jest wykonywana w ramach blokady, co oznacza, że zależy użytkownika, aby upewnić się, lotu w czasie przenoszenia nie ma żadnych zadań lekki. W przeciwnym razie sam liczne mogą wystąpić, prowadzące do wyjątków lub niespójny stan.

##  <a name="dtor"></a> ~ multitype_join

Niszczy `multitype_join` Blok obsługi wiadomości.

```
~multitype_join();
```

##  <a name="release"></a> Wydania

Zwalnia poprzedniego zastrzeżenie komunikatu pomyślnie.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu, zostały udostępnione.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `release` metody.

##  <a name="release_ref"></a> release_ref —

Zwalnia licznik odwołań, w tym `multiple_join` Blok obsługi wiadomości.

```
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana `ITarget` obiekt, który jest jest rozłączony z tego źródła. Blok źródłowy może zwolnić wszystkie zasoby, które są zarezerwowane dla blok docelowy.

##  <a name="reserve"></a> Zarezerwuj

Zarezerwowaniu wiadomości przez oferowane wcześniej to `multitype_join` Blok obsługi wiadomości.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` obiektu pozostaje zarezerwowane.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, która wywołuje `reserve` metody.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli komunikat został pomyślnie zarezerwowany, `false` inaczej. Rezerwacji może się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowane przez inny obiekt docelowy, źródła można odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu metody `reserve`, jeśli się powiedzie, należy wywołać albo `consume` lub `release` aby można było podjąć lub zrezygnować z posiadania wiadomości, odpowiednio.

##  <a name="unlink_target"></a> unlink_target —

Wstrzymuje blok docelowy z tego `multitype_join` Blok obsługi wiadomości.

```
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku można odłączyć od to `multitype_join` Blok obsługi wiadomości.

##  <a name="unlink_targets"></a> unlink_targets —

Wstrzymuje wszystkie elementy docelowe z tego `multitype_join` Blok obsługi wiadomości.

```
virtual void unlink_targets();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[choice, klasa](choice-class.md)<br/>
[join, klasa](join-class.md)
