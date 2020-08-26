---
title: 'Platform:: Array, Klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 00b73b9fb113066c6948c49ec7d2039748284800
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837763"
---
# <a name="platformarray-class"></a>Platform:: Array, Klasa

Reprezentuje jednowymiarową, modyfikowalną tablicę, którą można odbierać i przekazywać przez interfejs binarny aplikacji (ABI).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Elementy członkowskie

Platform:: Array dziedziczy wszystkie jej metody z [klasy platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) i implementuje `Value` Właściwość [platform:: IBoxArray](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktory tablic](#ctor)|Inicjuje jednowymiarową, modyfikowalną tablicę typów określonych przez parametr szablonu klasy, *T*.|

### <a name="methods"></a>Metody

Zobacz [Klasa platform:: WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Właściwości

| Nazwa | Opis |
|--|--|
| [Array:: value](#value) | Pobiera dojście do bieżącej tablicy. |

### <a name="remarks"></a>Uwagi

Klasa Array jest zapieczętowana i nie może być dziedziczona.

System typu środowisko wykonawcze systemu Windows nie obsługuje koncepcji tablic nieregularnych i w związku z tym nie można przekazać `IVector<Platform::Array<T>>` parametru jako wartości zwracanej lub metody. Aby przekazać nieregularną tablicę lub sekwencję sekwencji w ramach ABI, użyj `IVector<IVector<T>^>` .

Aby uzyskać więcej informacji o tym, kiedy i jak używać platform:: Array, zobacz [Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Ta klasa jest zdefiniowana w nagłówku vccorlib. h, który jest automatycznie dołączany do kompilatora. Jest on widoczny w technologii IntelliSense, ale nie w Przeglądarka obiektów, ponieważ nie jest typem publicznym zdefiniowanym w elemencie platform. winmd.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/zw**

## <a name="array-constructors"></a><a name="ctor"></a> Konstruktory tablic

Inicjuje jednowymiarową, modyfikowalną tablicę typów określonych przez parametr szablonu klasy, *T*.

## <a name="syntax"></a>Składnia

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametr szablonu klasy.

*zmienia*<br/>
Liczba elementów w tablicy.

*data*<br/>
Wskaźnik do tablicy danych typu `T` , który jest używany do inicjowania tego obiektu Array.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia wystąpień platform:: Array, zobacz [Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a> Array:: Get — Metoda

Pobiera odwołanie do elementu tablicy w określonej lokalizacji indeksu.

## <a name="syntax"></a>Składnia

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*index*<br/>
Indeks oparty na zero, który identyfikuje element w tablicy. Minimalny indeks to 0, a maksymalny indeks to wartość określona przez `size` parametr w [konstruktorze Array](#ctor).

### <a name="return-value"></a>Wartość zwracana

Element tablicy określony przez `index` parametr.

## <a name="arrayvalue-property"></a><a name="value"></a> Array:: Value — właściwość

Pobiera dojście do bieżącej tablicy.

## <a name="syntax"></a>Składnia

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do bieżącej tablicy.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
