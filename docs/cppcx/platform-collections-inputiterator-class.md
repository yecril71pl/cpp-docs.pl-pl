---
title: 'Platform:: Collections:: InputIterator, Klasa'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 4aeef07a34c04bd1ab47acf808026024faada567
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218432"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform:: Collections:: InputIterator, Klasa

Udostępnia standardową bibliotekę szablonów InputIterator dla kolekcji pochodzących od środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parametry

*Y*<br/>
Nazwa typu klasy szablonu InputIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora danych wejściowych (:: std:: input_iterator_tag).|
|`pointer`|Wskaźnik do`const X`|
|`reference`|Odwołanie do`const X`|
|`value_type`|`X`Nazwa typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[InputIterator:: InputIterator](#ctor)|Inicjuje nowe wystąpienie klasy InputIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator InputIterator:: operator! =](#operator-inequality)|Wskazuje, czy bieżący InputIterator nie jest równy określonemu InputIterator.|
|[InputIterator:: operator * — operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżącą InputIterator.|
|[Operator InputIterator:: operator + +](#operator-increment)|Zwiększa bieżącą InputIterator.|
|[InputIterator:: operator = = — operator](#operator-equality)|Wskazuje, czy bieżący InputIterator jest równy określonemu InputIterator.|
|[Operator InputIterator:: operator->](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący InputIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InputIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator:: InputIterator — Konstruktor

Inicjuje nowe wystąpienie klasy InputIterator.

### <a name="syntax"></a>Składnia

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parametry

*Iterator*<br/>
Obiekt iteratora.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Operator InputIterator:: operator- &gt;

Pobiera adres elementu określonego przez bieżącą InputIterator.

### <a name="syntax"></a>Składnia

```
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres elementu określonego przez bieżącą InputIterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>Operator InputIterator:: operator \*

Pobiera odwołanie do elementu określonego przez bieżącą InputIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący InputIterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator:: operator = = — operator

Wskazuje, czy bieżący InputIterator jest równy określonemu InputIterator.

### <a name="syntax"></a>Składnia

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny InputIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący InputIterator jest równy *innemu*; w przeciwnym razie **`false`** .

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>Operator InputIterator:: operator + +

Zwiększa bieżącą InputIterator.

### <a name="syntax"></a>Składnia

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżącą InputIterator. Druga składnia zwraca kopię bieżącego InputIterator, a następnie zwiększa bieżącą InputIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia InputIterator wstępnie zwiększa bieżącą InputIterator.

Druga składnia post-zwiększa bieżącą InputIterator. **`int`** Typ w drugiej składni wskazuje operację po przyrostie, a nie rzeczywisty argument operacji całkowitej.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>Operator InputIterator:: operator! =

Wskazuje, czy bieżący InputIterator nie jest równy określonemu InputIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny InputIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący InputIterator nie jest równy *innemu*; w przeciwnym razie **`false`** .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
