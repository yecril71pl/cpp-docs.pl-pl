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
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142032"
---
# <a name="itarget-class"></a>ITarget — Klasa

Klasa `ITarget` jest interfejsem dla wszystkich bloków docelowych. Bloki docelowe zużywają komunikaty oferowane przez `ISource` bloków.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych ładunku w komunikatach akceptowanych przez blok docelowy.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Publiczne definicje typów

|Name (Nazwa)|Opis|
|----------|-----------------|
|`filter_method`|Podpis dowolnej metody używanej przez blok, który zwraca wartość `bool`, aby określić, czy proponowany komunikat powinien zostać zaakceptowany.|
|`type`|Alias typu dla `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[~ ITarget destruktor](#dtor)|Niszczy obiekt `ITarget`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[rozpowszechni](#propagate)|Gdy jest zastępowany w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.|
|[Wyślij](#send)|Gdy jest zastępowany w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.|
|[supports_anonymous_source](#supports_anonymous_source)|Gdy jest zastępowany w klasie pochodnej, zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, które nie jest z nim połączone. Jeśli zastąpiona metoda zwraca **wartość true**, obiekt docelowy nie może odłożyć proponowanego komunikatu, ponieważ użycie przełożonego komunikatu w późniejszym czasie wymaga zidentyfikowania źródła w rejestrze linku źródłowego.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[link_source](#link_source)|Gdy jest zastępowany w klasie pochodnej, łączy określony blok źródłowy z tym blokiem `ITarget`.|
|[unlink_source](#unlink_source)|Gdy jest zastępowany w klasie pochodnej, odłącza określony blok źródłowy od tego bloku `ITarget`.|
|[unlink_sources](#unlink_sources)|Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki źródłowe z tego bloku `ITarget`.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [asynchroniczne bloki komunikatów](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ ITarget

Niszczy obiekt `ITarget`.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

Gdy jest zastępowany w klasie pochodnej, łączy określony blok źródłowy z tym blokiem `ITarget`.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Blok `ISource` połączony z tym blokiem `ITarget`.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana bezpośrednio w bloku `ITarget`. Bloki powinny być połączone ze sobą przy użyciu metody `link_target` w blokach `ISource`, co spowoduje wywołanie metody `link_source` w odpowiadającym jej miejscu docelowym.

## <a name="propagate"></a>rozpowszechni

Gdy jest zastępowany w klasie pochodnej, asynchronicznie przekazuje komunikat z bloku źródłowego do tego bloku docelowego.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PMessage` lub `_PSource` jest `NULL`.

## <a name="send"></a>Wyślij

Gdy jest zastępowany w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do obiektu `message`.

*_PSource*<br/>
Wskaźnik do bloku źródłowego oferującego komunikat.

### <a name="return-value"></a>Wartość zwrócona

[Message_status](concurrency-namespace-enums.md) wskazanie elementu docelowego, który zdecydował się wykonać wraz z wiadomością.

### <a name="remarks"></a>Uwagi

Metoda zgłasza wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , jeśli parametr `_PMessage` lub `_PSource` jest `NULL`.

Użycie metody `send` poza inicjacją komunikatu i propagowanie komunikatów w sieci jest niebezpieczne i może prowadzić do zakleszczenia.

Gdy `send` zwraca, wiadomość została już zaakceptowana i przekazana do bloku docelowego lub została odrzucona przez element docelowy.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Gdy jest zastępowany w klasie pochodnej, zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, które nie jest z nim połączone. Jeśli zastąpiona metoda zwraca **wartość true**, obiekt docelowy nie może odłożyć proponowanego komunikatu, ponieważ użycie przełożonego komunikatu w późniejszym czasie wymaga, aby źródło było identyfikowane w rejestrze z linkiem kwaśnym.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli blok może akceptować komunikat z źródła, które nie jest z nim **powiązane, w przeciwnym razie** .

## <a name="unlink_source"></a>unlink_source

Gdy jest zastępowany w klasie pochodnej, odłącza określony blok źródłowy od tego bloku `ITarget`.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Blok `ISource` jest odłączany od tego bloku `ITarget`.

### <a name="remarks"></a>Uwagi

Ta funkcja nie powinna być wywoływana bezpośrednio w bloku `ITarget`. Bloki powinny być rozłączone przy użyciu metod `unlink_target` lub `unlink_targets` w blokach `ISource`, które będą wywoływały metodę `unlink_source` w odpowiadającym jej miejscu docelowym.

## <a name="unlink_sources"></a>unlink_sources

Gdy jest zastępowany w klasie pochodnej, odłącza wszystkie bloki źródłowe z tego bloku `ITarget`.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ISource, klasa](isource-class.md)
