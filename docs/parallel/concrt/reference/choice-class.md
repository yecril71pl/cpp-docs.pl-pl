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
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142217"
---
# <a name="choice-class"></a>Klasa wyboru

Blok komunikatów `choice` jest blokiem pojedynczego źródła, który reprezentuje interakcję przepływu sterowania z zestawem źródeł. Blok wyboru czeka na jedno z wielu źródeł, aby utworzyć komunikat i propaguje indeks źródła, który wygenerował komunikat.

## <a name="syntax"></a>Składnia

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ oparty na `tuple`reprezentujący ładunki źródeł wejściowych.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Rozwiązanie](#ctor)|Przeciążone. Tworzy blok komunikatów `choice`.|
|[~ wybór destruktora](#dtor)|Niszczy blok komunikatów `choice`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[odebrać](#accept)|Akceptuje komunikat, który został zaoferowany przez ten blok `choice`, przez przeniesienie własności do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje liczbę odwołań w tym bloku komunikatów `choice`, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Wykorzystuje komunikat wcześniej oferowany przez ten blok komunikatów `choice` i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.|
|[has_value](#has_value)|Sprawdza, czy ten blok komunikatów `choice` został jeszcze zainicjowany z wartością.|
|[indeks](#index)|Zwraca indeks do `tuple` reprezentującego element wybrany przez blok komunikatów `choice`.|
|[link_target](#link_target)|Łączy blok docelowy z tym blokiem komunikatów `choice`.|
|[Usuwanie](#release)|Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.|
|[release_ref](#release_ref)|Zwalnia liczbę odwołań w tym bloku komunikatów `choice`.|
|[zarezerwować](#reserve)|Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `choice`.|
|[unlink_target](#unlink_target)|Odłącza blok docelowy z tego bloku komunikatów `choice`.|
|[unlink_targets](#unlink_targets)|Odłącza wszystkie elementy docelowe z tego bloku komunikatów `choice`. (Przesłania [ISource:: unlink_targets](isource-class.md#unlink_targets).)|
|[value](#value)|Pobiera komunikat, którego indeks został wybrany przez blok komunikatów `choice`.|

## <a name="remarks"></a>Uwagi

Blok wyboru zapewnia, że jest używana tylko jedna z komunikatów przychodzących.

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a>odebrać

Akceptuje komunikat, który został zaoferowany przez ten blok `choice`, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `accept`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

## <a name="acquire_ref"></a>acquire_ref

Uzyskuje liczbę odwołań w tym bloku komunikatów `choice`, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest połączony z tym źródłem podczas `link_target` metody.

## <a name="ctor"></a>Rozwiązanie

Tworzy blok komunikatów `choice`.

```cpp
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
Wybór `tuple` źródeł.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `choice`.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `choice`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

*_Choice*<br/>
Blok komunikatów `choice` do skopiowania. Należy zauważyć, że oryginalny obiekt jest oddzielony, co czyni ten konstruktor przenoszenia.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określisz parametrów `_PScheduler` lub `_PScheduleGroup`.

Konstrukcja przenoszenia nie jest przeprowadzana w ramach blokady, co oznacza, że jest ona dostępna dla użytkownika, aby upewnić się, że w czasie przenoszenia nie ma żadnych lekkich zadań. W przeciwnym razie może wystąpić wiele Races, co prowadzi do wyjątków lub niespójnego stanu.

## <a name="dtor"></a>~ wybór

Niszczy blok komunikatów `choice`.

```cpp
~choice();
```

## <a name="consume"></a>wykorzystania

Wykorzystuje komunikat wcześniej oferowany przez ten blok komunikatów `choice` i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zarezerwowanych obiektów `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `consume`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `message`, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Metoda `consume` jest podobna do `accept`, ale zawsze musi być poprzedzona wywołaniem `reserve` zwracającym **wartość true**.

## <a name="has_value"></a>has_value

Sprawdza, czy ten blok komunikatów `choice` został jeszcze zainicjowany z wartością.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli blok odebrał wartość, w przeciwnym razie **false** .

## <a name="index"></a>indeks

Zwraca indeks do `tuple` reprezentującego element wybrany przez blok komunikatów `choice`.

```cpp
size_t index();
```

### <a name="return-value"></a>Wartość zwrócona

Indeks komunikatów.

### <a name="remarks"></a>Uwagi

Ładunek wiadomości można wyodrębnić przy użyciu metody `get`.

## <a name="link_target"></a>link_target

Łączy blok docelowy z tym blokiem komunikatów `choice`.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku `ITarget`, aby połączyć ten blok komunikatów `choice`.

## <a name="release"></a>Usuwanie

Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` wydawany `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `release`.

## <a name="release_ref"></a>release_ref

Zwalnia liczbę odwołań w tym bloku komunikatów `choice`.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a>zarezerwować

Rezerwuje komunikat wcześniej oferowany przez ten blok komunikatów `choice`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` obiektu `message`, który jest zarezerwowany.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `reserve`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli komunikat został pomyślnie zarezerwowany, w przeciwnym razie **zwraca wartość false** . Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve`, jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu podjęcia lub zadawania wiadomości odpowiednio.

## <a name="unlink_target"></a>unlink_target

Odłącza blok docelowy z tego bloku komunikatów `choice`.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku `ITarget`, aby odłączyć od tego bloku komunikatów `choice`.

## <a name="unlink_targets"></a>unlink_targets

Odłącza wszystkie elementy docelowe z tego bloku komunikatów `choice`.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Uwagi

Ta metoda nie musi być wywoływana z destruktora, ponieważ destruktor dla wewnętrznego bloku `single_assignment` odłączy się prawidłowo.

## <a name="value"></a>wartościami

Pobiera komunikat, którego indeks został wybrany przez blok komunikatów `choice`.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Parametry

*_Payload_type*<br/>
Typ ładunku komunikatu.

### <a name="return-value"></a>Wartość zwrócona

Obciążenie komunikatu.

### <a name="remarks"></a>Uwagi

Ponieważ blok komunikatów `choice` może przyjmować dane wejściowe z różnymi typami ładunku, należy określić typ ładunku w punkcie pobierania. Możesz określić typ na podstawie wyniku metody `index`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[join, klasa](join-class.md)<br/>
[single_assignment, klasa](single-assignment-class.md)
