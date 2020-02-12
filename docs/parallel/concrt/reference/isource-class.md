---
title: ISource — Klasa
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139319"
---
# <a name="isource-class"></a>ISource — Klasa

Klasa `ISource` jest interfejsem dla wszystkich bloków źródłowych. Bloki źródłowe propagują komunikaty do bloków `ITarget`.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych ładunku w komunikatach wygenerowanych przez blok źródłowy.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`source_type`|Alias typu dla `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[~ ISource destruktor](#dtor)|Niszczy obiekt `ISource`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[odebrać](#accept)|Gdy jest zastępowany w klasie pochodnej, akceptuje komunikat, który został zaoferowany przez ten blok `ISource`, przenoszący własność do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Gdy jest zastępowany w klasie pochodnej, uzyskuje liczbę odwołań w tym bloku `ISource`, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Gdy jest zastępowany w klasie pochodnej, wykorzystuje komunikat wcześniej oferowany przez ten blok `ISource` i został pomyślnie zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.|
|[link_target](#link_target)|Gdy jest zastępowany w klasie pochodnej, łączy blok docelowy z tym blokiem `ISource`.|
|[Usuwanie](#release)|Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednie pomyślne rezerwacje komunikatów.|
|[release_ref](#release_ref)|Gdy jest zastępowany w klasie pochodnej, zwalnia liczbę odwołań w tym bloku `ISource`.|
|[zarezerwować](#reserve)|Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten blok `ISource`.|
|[unlink_target](#unlink_target)|Gdy jest zastępowany w klasie pochodnej, odłącza blok docelowy z tego bloku `ISource`, jeśli został znaleziony wcześniej połączony.|
|[unlink_targets](#unlink_targets)|Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki docelowe z tego bloku `ISource`.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a>odebrać

Gdy jest zastępowany w klasie pochodnej, akceptuje komunikat, który został zaoferowany przez ten blok `ISource`, przenoszący własność do obiektu wywołującego.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `accept`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

Metoda `accept` jest wywoływana przez obiekt docelowy, podczas gdy komunikat jest oferowany przez ten blok `ISource`. Zwrócony wskaźnik komunikatu może być inny niż przekazana do metody `propagate` bloku `ITarget`, jeśli to źródło zdecyduje się wykonać kopię wiadomości.

## <a name="acquire_ref"></a>acquire_ref

Gdy jest zastępowany w klasie pochodnej, uzyskuje liczbę odwołań w tym bloku `ISource`, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest połączony z tym źródłem podczas `link_target` metody.

## <a name="consume"></a>wykorzystania

Gdy jest zastępowany w klasie pochodnej, wykorzystuje komunikat wcześniej oferowany przez ten blok `ISource` i został pomyślnie zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="dtor"></a>~ ISource

Niszczy obiekt `ISource`.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

Gdy jest zastępowany w klasie pochodnej, łączy blok docelowy z tym blokiem `ISource`.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który jest połączony z tym blokiem `ISource`.

## <a name="release"></a>Usuwanie

Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednie pomyślne rezerwacje komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` zarezerwowanych obiektów `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `release`.

## <a name="release_ref"></a>release_ref

Gdy jest zastępowany w klasie pochodnej, zwalnia liczbę odwołań w tym bloku `ISource`.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez obiekt `ITarget`, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a>zarezerwować

Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten blok `ISource`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` oferowanego obiektu `message`.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje metodę `reserve`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli komunikat został pomyślnie zarezerwowany, w przeciwnym razie **zwraca wartość false** . Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve`, jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu podjęcia lub zadawania wiadomości odpowiednio.

## <a name="unlink_target"></a>unlink_target

Gdy jest zastępowany w klasie pochodnej, odłącza blok docelowy z tego bloku `ISource`, jeśli został znaleziony wcześniej połączony.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik prowadzący do odłączenia bloku docelowego z tego bloku `ISource`.

## <a name="unlink_targets"></a>unlink_targets

Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki docelowe z tego bloku `ISource`.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ITarget, klasa](itarget-class.md)
