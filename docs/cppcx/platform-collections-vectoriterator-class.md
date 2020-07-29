---
title: 'Platform:: Collections:: VectorIterator, Klasa'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: bade67a104774c3ab6187e250c6faf6969002c0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218419"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform:: Collections:: VectorIterator, Klasa

Zapewnia wzorzec standardowej biblioteki szablonów dla obiektów pochodzących z interfejsu środowisko wykonawcze systemu Windows IVector.

VectorIterator to iterator proxy, który przechowuje elementy typu VectorProxy \<T> . Jednak obiekt proxy jest prawie nigdy niewidoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Składnia

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu klasy szablonu VectorIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora dostępu losowego (:: std:: random_access_iterator_tag).|
|`pointer`|Wskaźnik do typu wewnętrznego, platform:: Collections::D etails:: VectorProxy \<T> , który jest wymagany dla implementacji VectorIterator.|
|`reference`|Odwołanie do typu wewnętrznego, platform:: Collections::D etails:: VectorProxy \<T> ,, który jest wymagany dla implementacji VectorIterator.|
|`value_type`|`T`Nazwa typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorIterator::VectorIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator VectorIterator:: operator-](#operator-minus)|Odejmuje określoną liczbę elementów od bieżącego iteratora, który uzyskuje nowy iterator, lub określony iterator z bieżącego iteratora zwracające liczbę elementów między iteratorami.|
|[VectorIterator:: operator--— operator](#operator-decrement)|Zmniejsza bieżącą VectorIterator.|
|[Operator VectorIterator:: operator! =](#operator-inequality)|Wskazuje, czy bieżący VectorIterator nie jest równy określonemu VectorIterator.|
|[VectorIterator:: operator * — operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżącą VectorIterator.|
|[VectorIterator:: operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określonym przemieszczeniem z bieżącego VectorIterator.|
|[VectorIterator:: operator + — operator](#operator-plus)|Zwraca VectorIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorIterator.|
|[Operator VectorIterator:: operator + +](#operator-increment)|Zwiększa bieżącą VectorIterator.|
|[Operator VectorIterator:: operator + =](#operator-plus-assign)|Zwiększa bieżącą VectorIterator według określonego przemieszczenia.|
|[VectorIterator:: operator — operator<](#operator-less-than)|Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.|
|[VectorIterator:: operator \< = — operator](#operator-less-than-or-equals)|Wskazuje, czy bieżąca VectorIterator jest mniejsza lub równa określonej VectorIterator.|
|[Operator VectorIterator:: operator-=](#operator-minus-equals)|Zmniejsza bieżącą VectorIterator przez określone przemieszczenie.|
|[VectorIterator:: operator = = — operator](#operator-equality)|Wskazuje, czy bieżący VectorIterator jest równy określonemu VectorIterator.|
|[VectorIterator:: operator — operator>](#operator-greater-than)|Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.|
|[Operator VectorIterator:: operator->](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący VectorIterator.|
|[VectorIterator:: operator>= — operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorIterator jest większy lub równy określonemu VectorIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Operator VectorIterator:: operator- &gt;

Pobiera adres elementu, do którego odwołuje się bieżący VectorIterator.

### <a name="syntax"></a>Składnia

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego odwołuje się bieżąca VectorIterator.

Typ wartości zwracanej jest nieokreślonym typem wewnętrznym, który jest wymagany dla implementacji tego operatora.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator:: operator--— operator

Zmniejsza bieżącą VectorIterator.

### <a name="syntax"></a>Składnia

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zmniejsza się, a następnie zwraca bieżącą VectorIterator. Druga składnia zwraca kopię bieżącego VectorIterator, a następnie zmniejsza bieżącą VectorIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorIterator wstępnie zmniejsza bieżącą VectorIterator.

Druga składnia post — zmniejsza bieżącą VectorIterator. **`int`** Typ w drugiej składni wskazuje operację po zmniejszeniu, a nie rzeczywisty argument operacji całkowitej.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>Operator VectorIterator:: operator \*

Pobiera adres elementu określonego przez bieżącą VectorIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator:: operator = = — operator

Wskazuje, czy bieżący VectorIterator jest równy określonemu VectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorIterator jest równy *innemu*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>Operator VectorIterator:: operator &gt;

Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorIterator jest większy niż *inny*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator:: operator &gt; = — operator

Wskazuje, czy bieżący VectorIterator jest większy lub równy określonemu VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorIterator jest większy lub równy *drugiemu*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>Operator VectorIterator:: operator + +

Zwiększa bieżącą VectorIterator.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżącą VectorIterator. Druga składnia zwraca kopię bieżącego VectorIterator, a następnie zwiększa bieżącą VectorIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorIterator wstępnie zwiększa bieżącą VectorIterator.

Druga składnia post-zwiększa bieżącą VectorIterator. **`int`** Typ w drugiej składni wskazuje operację po przyrostie, a nie rzeczywisty argument operacji całkowitej.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>Operator VectorIterator:: operator! =

Wskazuje, czy bieżący VectorIterator nie jest równy określonemu VectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorIterator nie jest równy *innemu*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>Operator VectorIterator:: operator &lt;

Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorIterator jest mniejszy niż *inny*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator:: operator &lt; = — operator

Wskazuje, czy bieżąca VectorIterator jest mniejsza lub równa określonej VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca VectorIterator jest mniejsza lub równa *innej*; w przeciwnym razie **`false`** .

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>Operator VectorIterator:: operator-

Odejmuje określoną liczbę elementów od bieżącego iteratora, który uzyskuje nowy iterator, lub określony iterator z bieżącego iteratora zwracające liczbę elementów między iteratorami.

### <a name="syntax"></a>Składnia

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Liczba elementów.

*różnych*<br/>
Inny VectorIterator.

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia operatora zwraca obiekt VectorIterator, który jest elementem `n` mniejszym od bieżącego VectorIterator. Druga składnia operatora zwraca liczbę elementów między bieżącą i `other` VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>Operator VectorIterator:: operator + =

Zwiększa bieżącą VectorIterator według określonego przemieszczenia.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowana VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator:: operator + — operator

Zwraca VectorIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorIterator.

### <a name="syntax"></a>Składnia

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
W drugiej składni atrybut TypeName VectorIterator.

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

*i*<br/>
W drugiej składni VectorIterator.

### <a name="return-value"></a>Wartość zwracana

W pierwszej składni element VectorIterator, który odwołuje się do elementu w określonym przemieszczenia z bieżącego VectorIterator.

W drugiej składni VectorIterator, który odwołuje się do elementu w określonym przemieszczenia od początku parametru `i` .

### <a name="remarks"></a>Uwagi

Przykład pierwszej składni

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>Operator VectorIterator:: operator-=

Zmniejsza bieżącą VectorIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowana VectorIterator.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator:: operator\[\]

Pobiera odwołanie do elementu, który jest określonym przemieszczeniem z bieżącego VectorIterator.

### <a name="syntax"></a>Składnia

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Element, który jest przemieszczenia przez `n` elementy z bieżącego VectorIterator.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>VectorIterator:: VectorIterator — Konstruktor

Inicjuje nowe wystąpienie klasy VectorIterator.

### <a name="syntax"></a>Składnia

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parametry

*v*<br/>
Obiekt IVector \<T> .

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni jest konstruktorem domyślnym. Drugim przykładem składni jest jawny Konstruktor, który jest używany do konstruowania elementu VectorIterator z \<T> obiektu IVector.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
