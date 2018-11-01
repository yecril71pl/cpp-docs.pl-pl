---
title: Platform::STAThreadAttribute, klasa
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
ms.openlocfilehash: 9073dc6e802aa2ed6bfa4fde2a09dd8a0864687b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555668"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute, klasa

Wskazuje, że model wątkowy dla aplikacji jest jednowątkowym (przedziale STA).

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

Dziedziczy atrybut STAThreadAttribute [Platform::Object, klasa](../cppcx/platform-object-class.md). STAThreadAttribute także przeciążenia lub ma następujące składowe:

|Nazwa|Opis|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|
|[STAThreadAttribute::ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** platformy

## <a name="ctor"></a> Konstruktor STAThreadAttribute

Inicjuje nowe wystąpienie klasy STAThreadAttribute.

### <a name="syntax"></a>Składnia

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

Określa, czy określony obiekt jest równy bieżącemu obiektowi.

### <a name="syntax"></a>Składnia

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parametry

*obj*<br/>
Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty są równe; w przeciwnym razie **false**.

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

Zwraca kod skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="tostring"></a> STAThreadAttribute::ToString

Zwraca ciąg, który reprezentuje bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg, który reprezentuje bieżący obiekt.

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)