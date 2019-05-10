---
title: Platform::Array, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: 94166dfcb222d5cfece146e7ad67bb04d6ad06e9
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221835"
---
# <a name="platformarray-class"></a>Platform::Array, klasa

Reprezentuje jednowymiarowo, którą można modyfikować tablicę, która jest odbierany i przekazywane między interfejsem binarnym aplikacji (ABI).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Elementy członkowskie

Platform::Array dziedziczy wszystkie metody z [Platform::WriteOnlyArray, klasa](../cppcx/platform-writeonlyarray-class.md) i implementuje `Value` właściwość [Platform::IBoxArray, interfejs](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktory tablicy](#ctor)|Inicjuje jednowymiarowo, którą można modyfikować tablicę typów określonej przez parametr szablonu klasy *T*.|

### <a name="methods"></a>Metody

Zobacz [Platform::WriteOnlyArray, klasa](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Właściwości

|||
|-|-|
|[Array::Value](#value)|Pobiera uchwyt do bieżącej tablicy.|

### <a name="remarks"></a>Uwagi

Array — klasa jest zapieczętowany i nie może być dziedziczona.

System typów środowiska wykonawczego Windows nie obsługuje pojęcie Tablice nieregularne i dlatego nie można przekazać IVector < Platform::Array\<T >> jako parametr zwracany wartość lub metody. Aby przekazać tablicę nieregularną lub sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.

Aby uzyskać więcej informacji na temat czasu i sposobu użycia Platform::Array, zobacz [tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Ta klasa jest zdefiniowana w nagłówku vccorlib.h, który jest automatycznie dołączany przez kompilator. Jest ona widoczna na technologii IntelliSense, ale nie w przeglądarce obiektów, ponieważ nie jest typem publicznym zdefiniowanym w platform.winmd.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: **/ZW**

## <a name="ctor"></a>  Konstruktory tablicy

Inicjuje jednowymiarowo, którą można modyfikować tablicę typów określonej przez parametr szablonu klasy *T*.

## <a name="syntax"></a>Składnia

```cpp
Array(unsigned int size);
Array(T* data, unsigned int size);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Parametr szablonu klasy.

*Rozmiar*<br/>
Liczba elementów w tablicy.

*data*<br/>
Wskaźnik do tablicy danych typu `T` używany do zainicjowania tego obiektu tablicy.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o sposobie tworzenia wystąpień Platform::Array, zobacz [tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>  Metoda Array::Get

Pobiera odwołanie do elementu tablicy w określonej lokalizacji indeksu.

## <a name="syntax"></a>Składnia

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera indeks, który identyfikuje element w tablicy. Minimalna indeks to 0, a maksymalna wartość indeksu jest wartość określoną przez `size` parametru w [Array — Konstruktor](#ctor).

### <a name="return-value"></a>Wartość zwracana

Określony przez element tablicy `index` parametru.

## <a name="value"></a>  Właściwość Array::Value

Pobiera uchwyt do bieżącej tablicy.

## <a name="syntax"></a>Składnia

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej tablicy.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
