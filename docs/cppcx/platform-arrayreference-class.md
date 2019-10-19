---
title: 'Platform:: ArrayReference, Klasa'
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: f7e587902f1c99b294ed79255397aeffccee26b5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587926"
---
# <a name="platformarrayreference-class"></a>Platform:: ArrayReference, Klasa

`ArrayReference` jest typem optymalizacji, który można zastąpić dla [platform:: Array ^](../cppcx/platform-array-class.md) w parametrach wejściowych, gdy chcesz wypełnić tablicę w stylu C danymi wejściowymi.

## <a name="syntax"></a>Składnia

```cpp
class ArrayReference
```

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ArrayReference::ArrayReference](#ctor)|Inicjuje nowe wystąpienie klasy `ArrayReference`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ArrayReference:: operator () — operator](#operator-call)|Konwertuje ten `ArrayReference` na `Platform::Array<T>^*`.|
|[ArrayReference:: operator = — operator](#operator-assign)|Przypisuje zawartość innego `ArrayReference` do tego wystąpienia.|

## <a name="exceptions"></a>Wyjątki

### <a name="remarks"></a>Uwagi

Przy użyciu `ArrayReference` do wypełnienia tablicy w stylu C, można uniknąć operacji dodatkowej kopiowania, która będzie dotyczyła kopiowania najpierw do zmiennej `Platform::Array`, a następnie do tablicy w stylu C. W przypadku korzystania z `ArrayReference` istnieje tylko jedna operacja kopiowania. Aby zapoznać się z przykładem kodu, zobacz [Array i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Nagłówek:** vccorlib. h

## <a name="ctor"></a>ArrayReference:: ArrayReference — Konstruktor

Inicjuje nowe wystąpienie klasy [platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) .

### <a name="syntax"></a>Składnia

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>Parametry

*dataArg*<br/>
Wskaźnik do danych macierzy.

*sizeArg*<br/>
Liczba elementów w tablicy źródłowej.

*otherArg*<br/>
Obiekt `ArrayReference`, którego dane zostaną przeniesione, aby zainicjować nowe wystąpienie.

### <a name="remarks"></a>Uwagi

## <a name="operator-assign"></a>ArrayReference:: operator = — operator

Przypisuje określony obiekt do bieżącego obiektu [platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) przy użyciu semantyki przenoszenia.

### <a name="syntax"></a>Składnia

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>Parametry

*otherArg*<br/>
Obiekt, który jest przenoszony do bieżącego obiektu `ArrayReference`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `ArrayReference`.

### <a name="remarks"></a>Uwagi

`Platform::ArrayReference` jest standardowym C++ szablonem klasy, a nie klasą referencyjną.

## <a name="operator-call"></a>ArrayReference:: operator () — operator

Konwertuje bieżący obiekt [platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) z powrotem na klasę [platform:: Array](../cppcx/platform-array-class.md) .

### <a name="syntax"></a>Składnia

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu `Array<TArg>^`

### <a name="remarks"></a>Uwagi

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md) jest standardowym C++ szablonem klasy, a [platform:: Array](../cppcx/platform-array-class.md) jest klasą ref.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
