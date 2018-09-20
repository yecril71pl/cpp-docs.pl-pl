---
title: Itarget — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4ada69fcd687d63022d0527ddf8da43906c483
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412018"
---
# <a name="itarget-class"></a>ITarget — Klasa

`ITarget` Klasy to interfejs dla wszystkich docelowych bloków. Bloków docelowych używanie wiadomości oferowane przez `ISource` bloków.

## <a name="syntax"></a>Składnia

```
template<class T>
class ITarget;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych ładunku w wiadomościach zaakceptowane przez blok docelowy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`filter_method`|Podpis metody używane przez blok, który zwraca `bool` wartość, aby określić, czy powinna być akceptowana oferowane wiadomości.|
|`type`|Alias typu `T`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~ ITarget — destruktor](#dtor)|Niszczy `ITarget` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[propagate](#propagate)|W przypadku przesłonięcia w klasie pochodnej, asynchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.|
|[Wyślij](#send)|W przypadku przesłonięcia w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.|
|[supports_anonymous_source](#supports_anonymous_source)|Po przesłonięciu w klasie pochodnej zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, który nie jest połączony do niego. Jeśli zwraca przeciążonej `true`, element docelowy nie mogą odkładać komunikat oferowane jako zużycia odroczony komunikat w późniejszym czasie wymaga źródła rozpoznawane w jego sourse łącze rejestru.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[link_source](#link_source)|W przypadku przesłonięcia w klasie pochodnej, łączy bloku określona źródłowa to `ITarget` bloku.|
|[unlink_source](#unlink_source)|W przypadku przesłonięcia w klasie pochodnej, rozłączysz bloku określonego źródła, z tego `ITarget` bloku.|
|[unlink_sources](#unlink_sources)|W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków źródła z tego `ITarget` bloku.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [bloki komunikatów asynchronicznych](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ITarget`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ ITarget

Niszczy `ITarget` obiektu.

```
virtual ~ITarget();
```

##  <a name="link_source"></a> link_source

W przypadku przesłonięcia w klasie pochodnej, łączy bloku określona źródłowa to `ITarget` bloku.

```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource` Blokowania jest połączona z tym `ITarget` bloku.

### <a name="remarks"></a>Uwagi

Ta funkcja nie należy wywoływać bezpośrednio na `ITarget` bloku. Bloki powinny być połączone ze sobą przy użyciu `link_target` metody `ISource` bloki, które będzie wywoływać `link_source` metody odpowiedniego obiektu docelowego.

##  <a name="propagate"></a> Propagacja

W przypadku przesłonięcia w klasie pochodnej, asynchronicznie przekazuje komunikat z blok źródłowy do tego bloku docelowego.

```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

##  <a name="send"></a> Wyślij

W przypadku przesłonięcia w klasie pochodnej, synchronicznie przekazuje komunikat do bloku docelowego.

```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Wskaźnik do `message` obiektu.

*_PSource*<br/>
Wskaźnik do blok źródłowy oferty wiadomości.

### <a name="return-value"></a>Wartość zwracana

A [message_status —](concurrency-namespace-enums.md) sygnał docelowy postanowiła zrobić z komunikatem.

### <a name="remarks"></a>Uwagi

Metoda zgłasza [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli `_PMessage` lub `_PSource` parametr `NULL`.

Za pomocą `send` metody poza inicjowania wiadomości i propagację wiadomości w sieci jest niebezpieczny i może prowadzić do zakleszczenia.

Gdy `send` zwraca komunikat albo już zostały zaakceptowane i przesłane do bloku docelowego lub została odrzucona przez element docelowy.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source —

Po przesłonięciu w klasie pochodnej zwraca wartość PRAWDA lub FAŁSZ w zależności od tego, czy blok komunikatów akceptuje komunikaty oferowane przez źródło, który nie jest połączony do niego. Jeśli zwraca przeciążonej `true`, element docelowy nie mogą odkładać komunikat oferowane jako zużycia odroczony komunikat w późniejszym czasie wymaga źródła rozpoznawane w jego sourse łącze rejestru.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli blok może zaakceptować komunikat ze źródła, która nie jest połączona z jej `false` inaczej.

##  <a name="unlink_source"></a> unlink_source

W przypadku przesłonięcia w klasie pochodnej, rozłączysz bloku określonego źródła, z tego `ITarget` bloku.

```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource` Blokowania jest rozłączony z tego `ITarget` bloku.

### <a name="remarks"></a>Uwagi

Ta funkcja nie należy wywoływać bezpośrednio na `ITarget` bloku. Można odłączyć bloki przy użyciu `unlink_target` lub `unlink_targets` metod `ISource` bloki, które będzie wywoływać `unlink_source` metody odpowiedniego obiektu docelowego.

##  <a name="unlink_sources"></a> unlink_sources

W przypadku przesłonięcia w klasie pochodnej, odłączenie wszystkich bloków źródła z tego `ITarget` bloku.

```
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[ISource, klasa](isource-class.md)
