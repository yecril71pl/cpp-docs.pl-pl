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
ms.openlocfilehash: df592e965b436ed5a1d60702f9e57088887d5a94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222709"
---
# <a name="isource-class"></a>ISource — Klasa

`ISource`Klasa jest interfejsem dla wszystkich bloków źródłowych. Bloki źródłowe propagują komunikaty do `ITarget` bloków.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w komunikatach wygenerowanych przez blok źródłowy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`source_type`|Alias typu dla `T` .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ ISource destruktor](#dtor)|Niszczy `ISource` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[odebrać](#accept)|Gdy jest zastępowany w klasie pochodnej, akceptuje komunikat, który był oferowany przez ten `ISource` blok, przekazując własność do obiektu wywołującego.|
|[acquire_ref](#acquire_ref)|Gdy jest zastępowany w klasie pochodnej, uzyskuje liczbę odwołań w tym `ISource` bloku, aby zapobiec usunięciu.|
|[wykorzystania](#consume)|Gdy jest zastępowany w klasie pochodnej, wykorzystuje komunikat wcześniej oferowany przez ten `ISource` blok i został pomyślnie zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.|
|[link_target](#link_target)|Gdy jest zastępowany w klasie pochodnej, łączy blok docelowy z tym `ISource` blokiem.|
|[Usuwanie](#release)|Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednie pomyślne rezerwacje komunikatów.|
|[release_ref](#release_ref)|Gdy jest zastępowany w klasie pochodnej, zwalnia liczbę odwołań w tym `ISource` bloku.|
|[zarezerwować](#reserve)|Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten `ISource` blok.|
|[unlink_target](#unlink_target)|Gdy jest zastępowany w klasie pochodnej, odłącza blok docelowy z tego `ISource` bloku, jeśli został znaleziony wcześniej połączony.|
|[unlink_targets](#unlink_targets)|Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki docelowe od tego `ISource` bloku.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ISource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="accept"></a><a name="accept"></a>odebrać

Gdy jest zastępowany w klasie pochodnej, akceptuje komunikat, który był oferowany przez ten `ISource` blok, przekazując własność do obiektu wywołującego.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `accept` metodę.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do komunikatu, którego obiekt wywołujący ma teraz własność.

### <a name="remarks"></a>Uwagi

`accept`Metoda jest wywoływana przez obiekt docelowy, podczas gdy komunikat jest oferowany przez ten `ISource` blok. Zwrócony wskaźnik komunikatu może być inny niż przekazana do `propagate` metody `ITarget` bloku, jeśli to źródło zdecyduje się wykonać kopię wiadomości.

## <a name="acquire_ref"></a><a name="acquire_ref"></a>acquire_ref

Gdy jest zastępowany w klasie pochodnej, uzyskuje liczbę odwołań w tym `ISource` bloku, aby zapobiec usunięciu.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest połączony z tym źródłem podczas tej `link_target` metody.

## <a name="consume"></a><a name="consume"></a>wykorzystania

Gdy jest zastępowany w klasie pochodnej, wykorzystuje komunikat wcześniej oferowany przez ten `ISource` blok i został pomyślnie zarezerwowany przez obiekt docelowy, przekazując własność do obiektu wywołującego.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="isource"></a><a name="dtor"></a>~ ISource

Niszczy `ISource` obiekt.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a><a name="link_target"></a>link_target

Gdy jest zastępowany w klasie pochodnej, łączy blok docelowy z tym `ISource` blokiem.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który jest połączony z tym `ISource` blokiem.

## <a name="release"></a><a name="release"></a>Usuwanie

Gdy jest zastępowany w klasie pochodnej, zwalnia poprzednie pomyślne rezerwacje komunikatów.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity`Obiekt zastrzeżony `message` .

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `release` metodę.

## <a name="release_ref"></a><a name="release_ref"></a>release_ref

Gdy jest zastępowany w klasie pochodnej, zwalnia liczbę odwołań w tym `ISource` bloku.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje tę metodę.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez `ITarget` obiekt, który jest odłączany od tego źródła. Blok źródłowy może zwolnić wszystkie zasoby zarezerwowane dla bloku docelowego.

## <a name="reserve"></a><a name="reserve"></a>zarezerwować

Gdy jest zastępowany w klasie pochodnej, rezerwuje komunikat wcześniej oferowany przez ten `ISource` blok.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Dla `runtime_object_identity` oferowanego `message` obiektu.

*_PTarget*<br/>
Wskaźnik do bloku docelowego, który wywołuje `reserve` metodę.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli komunikat został pomyślnie zarezerwowany, **`false`** w przeciwnym razie. Rezerwacje mogą się nie powieść z wielu powodów, takich jak: komunikat został już zarezerwowany lub zaakceptowany przez inny obiekt docelowy, źródło może odmówić rezerwacji i tak dalej.

### <a name="remarks"></a>Uwagi

Po wywołaniu `reserve` , jeśli zakończy się powodzeniem, należy wywołać `consume` lub `release` w celu przeprowadzenia lub zadawać swój komunikat odpowiednio.

## <a name="unlink_target"></a><a name="unlink_target"></a>unlink_target

Gdy jest zastępowany w klasie pochodnej, odłącza blok docelowy z tego `ISource` bloku, jeśli został znaleziony wcześniej połączony.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Wskaźnik prowadzący do odłączenia bloku docelowego z tego `ISource` bloku.

## <a name="unlink_targets"></a><a name="unlink_targets"></a>unlink_targets

Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki docelowe od tego `ISource` bloku.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa ITarget](itarget-class.md)
