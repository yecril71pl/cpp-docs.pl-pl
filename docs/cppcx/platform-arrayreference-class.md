---
title: Platform::ArrayReference, klasa
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: e9dd16ad6c3f53c5562b0419197a582c06fbc642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354790"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference, klasa

`ArrayReference`jest typem optymalizacji, który można zastąpić [platformą::Array^](../cppcx/platform-array-class.md) w parametrach wejściowych, gdy chcesz wypełnić tablicę w stylu C danymi wejściowymi.

## <a name="syntax"></a>Składnia

```cpp
class ArrayReference
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wniosek o tablicę::Odniesienie do tablic](#ctor)|Inicjuje nowe wystąpienie klasy `ArrayReference`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ArrayReference::operator() Operator](#operator-call)|Konwertuje `ArrayReference` to `Platform::Array<T>^*`na .|
|[ArrayReference::operator= Operator](#operator-assign)|Przypisuje zawartość innego `ArrayReference` do tego wystąpienia.|

## <a name="exceptions"></a>Wyjątki

### <a name="remarks"></a>Uwagi

Za `ArrayReference` pomocą do wypełnienia tablicy w stylu C, można uniknąć dodatkowej operacji `Platform::Array` kopiowania, które byłyby zaangażowane w kopiowanie najpierw do zmiennej, a następnie do tablicy w stylu C. Podczas korzystania `ArrayReference`z programu jest tylko jedna operacja kopiowania. Przykładowy kod można znaleźć w [000 000 000 000 000 000 000 000 000 0](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Nagłówek:** vccorlib.h

## <a name="arrayreferencearrayreference-constructor"></a><a name="ctor"></a>ArrayReference::Konstruktor liczby odwołań tablic

Inicjuje nowe wystąpienie [klasy Platform::ArrayReference.](../cppcx/platform-arrayreference-class.md)

### <a name="syntax"></a>Składnia

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parametry

*daneArg*<br/>
Wskaźnik do danych tablicy.

*rozmiarArg*<br/>
Liczba elementów w tablicy źródłowej.

*inneArg*<br/>
Obiekt, `ArrayReference` którego dane zostaną przeniesione do zainicjowania nowego wystąpienia.

### <a name="remarks"></a>Uwagi

## <a name="arrayreferenceoperator-operator"></a><a name="operator-assign"></a>ArrayReference::operator= Operator

Przypisuje określony obiekt do bieżącego [obiektu Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) przy użyciu semantyki przenoszenia.

### <a name="syntax"></a>Składnia

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parametry

*inneArg*<br/>
Obiekt, który jest przenoszony do bieżącego `ArrayReference` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `ArrayReference`.

### <a name="remarks"></a>Uwagi

`Platform::ArrayReference`jest szablonem klasy c++, a nie klasą ref.

## <a name="arrayreferenceoperator-operator"></a><a name="operator-call"></a>ArrayReference::operator() Operator

Konwertuje bieżący [obiekt Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) z powrotem na [platformę::Klasa Array.](../cppcx/platform-array-class.md)

### <a name="syntax"></a>Składnia

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do obiektu typu`Array<TArg>^`

### <a name="remarks"></a>Uwagi

[Platforma::ArrayReference](../cppcx/platform-arrayreference-class.md) jest standardowym szablonem klasy C++, a [Platform::Array](../cppcx/platform-array-class.md) jest klasą ref.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
