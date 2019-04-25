---
title: Platform::ArrayReference, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: 923f60e90517e377b99d5e29f38c48b2633c3c46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161574"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference, klasa

`ArrayReference` jest typem optymalizacji, który można podstawić [Platform::Array ^](../cppcx/platform-array-class.md) w parametrów wejściowych, gdy chcesz wypełnić tablicy stylu C z danymi wejściowymi.

## <a name="syntax"></a>Składnia

```cpp
class ArrayReference
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Inicjuje nowe wystąpienie klasy `ArrayReference` klasy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ArrayReference::operator() Operator](#operator-call)|Konwertuje to `ArrayReference` do `Platform::Array<T>^*`.|
|[ArrayReference::operator = — Operator](#operator-assign)|Przypisuje zawartość innego `ArrayReference` dla tego wystąpienia.|

## <a name="exceptions"></a>Wyjątki

### <a name="remarks"></a>Uwagi

Za pomocą `ArrayReference` do wypełnienia tablicy stylu C, można uniknąć operacja kopiowania dodatkowych może brać udział w kopiowania najpierw `Platform::Array` zmiennej, a następnie do tablicy stylu C. Kiedy używasz `ArrayReference`, istnieje tylko jedna kopia operacja. Dla przykładu kodu zobacz [tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Nagłówek:** vccorlib.h

## <a name="ctor"></a>  Konstruktor ArrayReference::ArrayReference

Inicjuje nowe wystąpienie klasy [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) klasy.

### <a name="syntax"></a>Składnia

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parametry

*dataArg*<br/>
Wskaźnik do danych.

*sizeArg*<br/>
Liczba elementów w tablicy źródłowej.

*otherArg*<br/>
`ArrayReference` Obiektu, którego dane zostaną przeniesione do inicjuje nowe wystąpienie.

### <a name="remarks"></a>Uwagi

## <a name="operator-assign"></a>  ArrayReference::operator = — Operator

Przypisuje określony obiekt do bieżącego [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) , używając semantyki przenoszenia obiektu.

### <a name="syntax"></a>Składnia

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parametry

*otherArg*<br/>
Obiekt, który jest przenoszony do bieżącego `ArrayReference` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `ArrayReference`.

### <a name="remarks"></a>Uwagi

`Platform::ArrayReference` jest standardowego szablonu klasy C++, a nie klasy referencyjnej.

## <a name="operator-call"></a>  ArrayReference::operator() Operator

Konwertuje aktualny [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) obiektu do [Platform::Array](../cppcx/platform-array-class.md) klasy.

### <a name="syntax"></a>Składnia

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu `Array<TArg>^`

### <a name="remarks"></a>Uwagi

[Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) i [Platform::Array](../cppcx/platform-array-class.md) są standardowe szablony klas języka C++, ref nie klasami.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
