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
ms.openlocfilehash: a5b9bc26b6d9ec66dc74e7adaad31eea1eece118
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224984"
---
# <a name="choice-class"></a>Klasa wyboru

`choice`Blok komunikatów jest blokiem pojedynczego źródła, który reprezentuje interakcję przepływu sterowania z zestawem źródeł. Blok wyboru czeka na jedno z wielu źródeł, aby utworzyć komunikat i propaguje indeks źródła, który wygenerował komunikat.

## <a name="syntax"></a>Składnia

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
`tuple`Typ oparty na liczbie ładunków źródeł wejściowych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`type`|Alias typu dla `T` .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Rozwiązanie](#ctor)|Przeciążone. Tworzy `choice` blok komunikatów.|
|[~ wybór destruktora](#dtor)|Niszczy `choice` blok komunikatów.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[odebrać](#accept)|Akceptuje komunikat, który był oferowany przez ten `choice` blok, przekazując własność do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Uzyskuje liczbę odwołań w tym `choice` bloku komunikatów, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Wykorzystuje komunikat wcześniej oferowany przez ten `choice` blok komunikatów i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.|
|[has_value](#has_value)|Sprawdza, czy ten `choice` blok komunikatów został jeszcze zainicjowany z wartością.|
|[indeks](#index)|Zwraca indeks `tuple` reprezentujący element wybrany przez `choice` blok komunikatów.|
|[link_target](#link_target)|Łączy blok docelowy z tym `choice` blokiem obsługi komunikatów.|
|[Usuwanie](#release)|Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.|
|[release_ref](#release_ref)|Zwalnia liczbę odwołań w tym `choice` bloku komunikatów.|
|[zarezerwować](#reserve)|Rezerwuje komunikat wcześniej oferowany przez ten `choice` blok komunikatów.|
|[unlink_target](#unlink_target)|Odłącza blok docelowy z tego `choice` bloku komunikatów.|
|[unlink_targets](#unlink_targets)|Odłącza wszystkie elementy docelowe z tego `choice` bloku komunikatów. (Przesłania [ISource:: unlink_targets](isource-class.md#unlink_targets).)|
|[wartościami](#value)|Pobiera komunikat, którego indeks został wybrany przez `choice` blok komunikatów.|

## <a name="remarks"></a>Uwagi

Blok wyboru zapewnia, że jest używana tylko jedna z komunikatów przychodzących.

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a><a name="accept"></a>odebrać

Akceptuje komunikat, który był oferowany przez ten `choice` blok, przekazując własność do obiektu wywołującego.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `accept` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

Uzyskuje liczbę odwołań w tym `choice` bloku komunikatów, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączony z tym źródłem podczas tej `link_target` metody.

## <a name="choice"></a><a name="ctor"></a>Rozwiązanie

Tworzy `choice` blok komunikatów.

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
Z `tuple` wybranych źródeł.

*_PScheduler*<br/>
`Scheduler`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `choice` bloku obsługi komunikatów.

*_PScheduleGroup*<br/>
`ScheduleGroup`Obiekt, w ramach którego zaplanowano zadanie propagacji dla `choice` bloku obsługi komunikatów. `Scheduler`Używany obiekt jest implikowany przez grupę harmonogramów.

*_Choice*<br/>
`choice`Blok komunikatów do skopiowania. Należy zauważyć, że oryginalny obiekt jest oddzielony, co czyni ten konstruktor przenoszenia.

### <a name="remarks"></a>Uwagi

Środowisko uruchomieniowe używa domyślnego harmonogramu, jeśli nie określono `_PScheduler` `_PScheduleGroup` parametrów lub.

Konstrukcja przenoszenia nie jest przeprowadzana w ramach blokady, co oznacza, że jest ona dostępna dla użytkownika, aby upewnić się, że w czasie przenoszenia nie ma żadnych lekkich zadań. W przeciwnym razie może wystąpić wiele Races, co prowadzi do wyjątków lub niespójnego stanu.

## <a name="choice"></a><a name="dtor"></a>~ wybór

Niszczy `choice` blok komunikatów.

```cpp
~choice();
```

## <a name="consume"></a><a name="consume"></a>wykorzystania

Wykorzystuje komunikat wcześniej oferowany przez ten `choice` blok komunikatów i został pomyślnie zarezerwowany przez obiekt docelowy, przez przeniesienie własności do obiektu wywołującego.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity`Obiekt zastrzeżony `message` .

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `consume` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `message` obiektu, do którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

`consume`Metoda jest podobna do `accept` , ale musi być zawsze poprzedzona wywołaniem `reserve` zwracanym **`true`** .

## <a name="has_value"></a><a name="has_value"></a>has_value

Sprawdza, czy ten `choice` blok komunikatów został jeszcze zainicjowany z wartością.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli blok odebrał wartość, **`false`** w przeciwnym razie.

## <a name="index"></a><a name="index"></a>indeks

Zwraca indeks `tuple` reprezentujący element wybrany przez `choice` blok komunikatów.

```cpp
size_t index();
```

### <a name="return-value"></a>Wartość zwracana

Indeks komunikatów.

### <a name="remarks"></a>Uwagi

Ładunek wiadomości można wyodrębnić przy użyciu `get` metody.

## <a name="link_target"></a><a name="link_target"></a>link_target

Łączy blok docelowy z tym `choice` blokiem obsługi komunikatów.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku do łączenia z tym `choice` blokiem obsługi komunikatów.

## <a name="release"></a><a name="release"></a>Usuwanie

Zwalnia poprzednie pomyślne zastrzeżenie dotyczące komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` `message` Wydawany obiekt.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `release` metodę.

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

Zwalnia liczbę odwołań w tym `choice` bloku komunikatów.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a><a name="reserve"></a>zarezerwować

Rezerwuje komunikat wcześniej oferowany przez ten `choice` blok komunikatów.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Obiekt, który jest `runtime_object_identity` `message` zarezerwowany.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `reserve` metodę.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie. Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve` , jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu przeprowadzenia lub zadawać swój komunikat odpowiednio.

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

Odłącza blok docelowy z tego `choice` bloku komunikatów.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do `ITarget` bloku do odłączenia od tego `choice` bloku komunikatów.

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

Odłącza wszystkie elementy docelowe z tego `choice` bloku komunikatów.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Uwagi

Ta metoda nie musi być wywoływana z destruktora, ponieważ destruktor `single_assignment` bloku wewnętrznego odłączy się prawidłowo.

## <a name="value"></a><a name="value"></a>wartościami

Pobiera komunikat, którego indeks został wybrany przez `choice` blok komunikatów.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Parametry

*_Payload_type*<br/>
Typ ładunku komunikatu.

### <a name="return-value"></a>Wartość zwracana

Ładunek wiadomości.

### <a name="remarks"></a>Uwagi

Ponieważ `choice` blok komunikatów może przyjmować dane wejściowe z różnymi typami ładunku, należy określić typ ładunku w punkcie pobierania. Możesz określić typ na podstawie wyniku `index` metody.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[join — Klasa](join-class.md)<br/>
[Klasa single_assignment](single-assignment-class.md)
