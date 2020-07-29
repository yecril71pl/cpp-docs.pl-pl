---
title: 'Platform:: STAThreadAttribute, Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 6a8220d8cddca29e621b21fc56966efdb42cb32e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213024"
---
# <a name="platformstathreadattribute-class"></a>Platform:: STAThreadAttribute, Klasa

Wskazuje, że model wątkowości dla aplikacji jest apartamentem jednowątkowym (STA).

## <a name="syntax"></a>Składnia

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor STAThreadAttribute 1](#ctor)|Inicjuje nowe wystąpienie klasy.|

### <a name="public-methods"></a>Metody publiczne

Atrybut STAThreadAttribute dziedziczy z [klasy platform:: Object](../cppcx/platform-object-class.md). STAThreadAttribute również przeciążać lub ma następujących członków:

|Nazwa|Opis|
|----------|-----------------|
|[STAThreadAttribute:: Equals](#equals)|Określa, czy dany obiekt jest taki sam, jak bieżący obiekt.|
|[STAThreadAttribute:: GetHashCode](#gethashcode)|Zwraca wartość skrótu dla tego wystąpienia.|
|[STAThreadAttribute:: ToString](#tostring)|Zwraca ciąg reprezentujący bieżący obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platformach

## <a name="stathreadattribute-constructor"></a><a name="ctor"></a>Konstruktor STAThreadAttribute

Inicjuje nowe wystąpienie klasy STAThreadAttribute.

### <a name="syntax"></a>Składnia

```cpp
public:STAThreadAttribute();
```

## <a name="stathreadattributeequals"></a><a name="equals"></a>STAThreadAttribute:: Equals

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

## <a name="stathreadattributegethashcode"></a><a name="gethashcode"></a>STAThreadAttribute:: GetHashCode

Zwraca wartość skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="stathreadattributetostring"></a><a name="tostring"></a>STAThreadAttribute:: ToString

Zwraca ciąg reprezentujący bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg reprezentujący bieżący obiekt.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
