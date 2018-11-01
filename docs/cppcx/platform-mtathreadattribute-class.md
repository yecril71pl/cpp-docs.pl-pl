---
title: Platform::MTAThreadAttribute, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 07a20457df1bb9124b965cfae27d30e9f31d7531
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528079"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute, klasa

Wskazuje, że model wątkowy dla aplikacji jest wielowątkowej (MTA).

## <a name="syntax"></a>Składnia

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[1 Konstruktor MTAThreadAttribute](#ctor) konstruktora|Inicjuje nowe wystąpienie klasy.|

### <a name="public-methods"></a>Metody publiczne

Dziedziczy atrybut MTAThreadAttribute [Platform::Object, klasa](../cppcx/platform-object-class.md). MTAThreadAttribute także przeciążenia lub ma następujące składowe:

|Nazwa|Opis|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Określa, czy określony obiekt jest równy bieżącemu obiektowi.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Zwraca kod skrótu dla tego wystąpienia.|
|[MTAThreadAttribute::ToString](#tostring)|Zwraca ciąg, który reprezentuje bieżący obiekt.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Metadane:** platform.winmd

**Namespace:** platformy

## <a name="ctor"></a> Konstruktor MTAThreadAttribute

Inicjuje nowe wystąpienie klasy MTAThreadAttribute.

### <a name="syntax"></a>Składnia

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

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

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

Zwraca kod skrótu dla tego wystąpienia.

### <a name="syntax"></a>Składnia

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Wartość zwracana

Kod skrótu dla tego wystąpienia.

## <a name="tostring"></a> MTAThreadAttribute::ToString

Zwraca ciąg, który reprezentuje bieżący obiekt.

### <a name="syntax"></a>Składnia

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg, który reprezentuje bieżący obiekt.

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)