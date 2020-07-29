---
title: ITarget — Klasa
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: 39aebd9d82f098225c1275ac6f43d64fc1ce3ba8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231718"
---
# <a name="itarget-class"></a>ITarget — Klasa

`ITarget`Klasa jest interfejsem dla wszystkich bloków docelowych. Bloki docelowe zużywają komunikaty oferowane im przez `ISource` bloki.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w komunikatach akceptowanych przez blok docelowy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`filter_method`|Podpis dowolnej metody używanej przez blok, który zwraca wartość, **`bool`** Aby określić, czy proponowany komunikat powinien zostać zaakceptowany.|
|`type`|Alias typu dla `T` .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ ITarget destruktor](#dtor)|Niszczy `ITarget` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[rozpowszechni](#propagate)|Gdy jest zastępowany w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|
|[Wyślij](#send)|Gdy jest zastępowany w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.|
|[supports_anonymous_source](#supports_anonymous_source)|Gdy jest zastępowany w klasie pochodnej, zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, które nie jest z nim połączone. Jeśli zastąpiona metoda zwraca **`true`** , obiekt docelowy nie może odłożyć proponowanego komunikatu, ponieważ użycie przełożonego komunikatu w późniejszym czasie wymaga, aby źródło było identyfikowane w rejestrze linków źródłowych.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[link_source](#link_source)|Gdy jest zastępowany w klasie pochodnej, łączy określony blok źródłowy z tym `ITarget` blokiem.|
|[unlink_source](#unlink_source)|Gdy jest zastępowany w klasie pochodnej, odłącza określony blok źródłowy od tego `ITarget` bloku.|
|[unlink_sources](#unlink_sources)|Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki źródłowe od tego `ITarget` bloku.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="itarget"></a><a name="dtor"></a>~ ITarget

Niszczy `ITarget` obiekt.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a><a name="link_source"></a>link_source

Gdy jest zastępowany w klasie pochodnej, łączy określony blok źródłowy z tym `ITarget` blokiem.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource`Blok połączony z tym `ITarget` blokiem.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana bezpośrednio w `ITarget` bloku. Bloki powinny być połączone przy użyciu `link_target` metody w `ISource` blokach, co spowoduje wywołanie `link_source` metody w odpowiadającym jej miejscu docelowym.

## <a name="propagate"></a><a name="propagate"></a>rozpowszechni

Gdy jest zastępowany w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli `_PMessage` `_PSource` parametr lub jest `NULL` .

## <a name="send"></a><a name="send"></a>Wyślij

Gdy jest zastępowany w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwracana

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli `_PMessage` `_PSource` parametr lub jest `NULL` .

Użycie `send` metody poza inicjacją komunikatów i propagowanie komunikatów w sieci jest niebezpieczne i może prowadzić do zakleszczenia.

Gdy `send` zwraca, wiadomość została już zaakceptowana i przekazana do bloku docelowego lub została odrzucona przez element docelowy.

## <a name="supports_anonymous_source"></a><a name="supports_anonymous_source"></a>supports_anonymous_source

Gdy jest zastępowany w klasie pochodnej, zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, które nie jest z nim połączone. Jeśli zastąpiona metoda zwraca **`true`** , obiekt docelowy nie może odłożyć proponowanego komunikatu, ponieważ użycie przełożonego komunikatu w późniejszym czasie wymaga, aby źródło było identyfikowane w rejestrze linku do zasobów.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli blok może akceptować komunikat z źródła, które nie jest z nim połączone **`false`** .

## <a name="unlink_source"></a><a name="unlink_source"></a>unlink_source

Gdy jest zastępowany w klasie pochodnej, odłącza określony blok źródłowy od tego `ITarget` bloku.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource`Blok jest odłączany od tego `ITarget` bloku.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana bezpośrednio w `ITarget` bloku. Bloki powinny być rozłączone przy `unlink_target` użyciu `unlink_targets` metod lub w `ISource` blokach, które będą wywoływały `unlink_source` metodę w odpowiadającym jej miejscu docelowym.

## <a name="unlink_sources"></a><a name="unlink_sources"></a>unlink_sources

Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki źródłowe od tego `ITarget` bloku.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[Klasa ISource](isource-class.md)
