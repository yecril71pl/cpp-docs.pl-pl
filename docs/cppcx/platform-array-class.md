---
title: Platform::Array, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Array
- VCCORLIB/Platform::Array::Value
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
ms.openlocfilehash: d625d80df67a3c8207467ad629afd4c2bf88db18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318653"
---
# <a name="platformarray-class"></a>Platform::Array, klasa

Reprezentuje jednowymiarową, modyfikowalną tablicę, która może być odbierana i przekazywana przez interfejs binarny aplikacji (ABI).

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
private ref class Array<TArg, 1> :
    public WriteOnlyArray<TArg, 1>,
    public IBoxArray<TArg>
```

### <a name="members"></a>Elementy członkowskie

Platforma::Array dziedziczy wszystkie swoje metody z [platformy::WriteOnlyArray Class](../cppcx/platform-writeonlyarray-class.md) i implementuje `Value` właściwość [platformy::IBoxArray Interface](../cppcx/platform-iboxarray-interface.md).

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktory tablic](#ctor)|Inicjuje jednowymiarową, modyfikowalną tablicę typów określonych przez parametr szablonu klasy, *T*.|

### <a name="methods"></a>Metody

Zobacz [platforma::WriteOnlyArray Class](../cppcx/platform-writeonlyarray-class.md).

### <a name="properties"></a>Właściwości

|||
|-|-|
|[Tablica::Wartość](#value)|Pobiera dojście do bieżącej tablicy.|

### <a name="remarks"></a>Uwagi

Array Klasa jest zapieczętowany i nie mogą być dziedziczone.

System typu środowiska wykonawczego systemu Windows nie obsługuje koncepcji postrzępionych tablic i dlatego nie można przekazać\<IVector<Platform::Array T>> jako wartość zwracaną lub parametr metody. Aby przekazać postrzępioną tablicę lub sekwencję `IVector<IVector<T>^>`sekwencji w całej ABI, użyj .

Aby uzyskać więcej informacji o tym, kiedy i jak korzystać z platformy::Tablica, zobacz [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

Ta klasa jest zdefiniowana w nagłówku vccorlib.h, który jest automatycznie uwzględniany przez kompilator. Jest on widoczny w intellisense, ale nie w przeglądarce obiektów, ponieważ nie jest to typ publiczny zdefiniowany w platform.winmd.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/ZW**

## <a name="array-constructors"></a><a name="ctor"></a>Konstruktory tablic

Inicjuje jednowymiarową, modyfikowalną tablicę typów określonych przez parametr szablonu klasy, *T*.

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

*Danych*<br/>
Wskaźnik do tablicy danych `T` typu, który jest używany do inicjowania tego obiektu Array.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia wystąpień platformy::Array, zobacz [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="arrayget-method"></a><a name="get"></a>Tablica::pobierz metodę

Pobiera odwołanie do elementu tablicy w określonej lokalizacji indeksu.

## <a name="syntax"></a>Składnia

```cpp
T& get(unsigned int index)  const;
```

#### <a name="parameters"></a>Parametry

*Indeks*<br/>
Indeks od zera, który identyfikuje element w tablicy. Minimalny indeks wynosi 0, a maksymalny indeks `size` jest wartością określoną przez parametr w [konstruktorze array](#ctor).

### <a name="return-value"></a>Wartość zwracana

Element tablicy określony `index` przez parametr.

## <a name="arrayvalue-property"></a><a name="value"></a>Tablica::Właściwość value

Pobiera dojście do bieżącej tablicy.

## <a name="syntax"></a>Składnia

```cpp
property Array^ Value;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do bieżącej tablicy.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)<br/>
[Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
