---
title: 'Platform:: MTAThreadAttribute, Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 700eeae226be48c1f6659d621f2f5c0ed397bb7f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213050"
---
# <a name="platformmtathreadattribute-class"></a>Platform:: MTAThreadAttribute, Klasa

Wskazuje, że model wątkowości dla aplikacji jest apartamentem wielowątkowym (MTA).

## <a name="syntax"></a>Składnia

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|Konstruktor [MTAThreadAttribute 1](#ctor)|Inicjuje nowe wystąpienie klasy.|

### <a name="public-methods"></a>Metody publiczne

Atrybut MTAThreadAttribute dziedziczy z [klasy platform:: Object](../cppcx/platform-object-class.md). MTAThreadAttribute również przeciążać lub ma następujących członków:

|Nazwa|Opis|
|----------|-----------------|
|[MTAThreadAttribute:: Equals](#equals)|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.|
|[MTAThreadAttribute:: GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[MTAThreadAttribute:: ToString](#tostring)|Zwraca ciąg reprezentujący bieżący obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Metadane:** obiekt platform. winmd

**Przestrzeń nazw:** Platformach

## <a name="mtathreadattribute-constructor"></a><a name="ctor"></a>Konstruktor MTAThreadAttribute

Inicjuje nowe wystąpienie klasy MTAThreadAttribute.

### <a name="syntax"></a>Składnia

```cpp
public:MTAThreadAttribute();
```

## <a name="mtathreadattributeequals"></a><a name="equals"></a>MTAThreadAttribute:: Equals

Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parametry

*obiektów*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty są równe; w przeciwnym razie **`false`** .

## <a name="mtathreadattributegethashcode"></a><a name="gethashcode"></a>MTAThreadAttribute:: GetHashCode

Zwraca wartość skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="mtathreadattributetostring"></a><a name="tostring"></a>MTAThreadAttribute:: ToString

Zwraca ciąg reprezentujący bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg reprezentujący bieżący obiekt.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
