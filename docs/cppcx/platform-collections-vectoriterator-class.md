---
title: Platform::Collections::VectorIterator, klasa
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: e649027c2ba3f637c42765af691f4d321913fb28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354366"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator, klasa

Udostępnia iterator biblioteki szablonów standardowych dla obiektów pochodzących z interfejsu IVector środowiska wykonawczego systemu Windows.

VectorIterator jest iteratorem proxy, który przechowuje elementy\<typu VectorProxy T>. Jednak obiekt proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [Kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Składnia

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu klasy szablonu VectorIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora dostępu losowego (::std::random_access_iterator_tag).|
|`pointer`|Wskaźnik do typu wewnętrznego, Platform::Collections::Details::VectorProxy\<T>, który jest wymagany do implementacji VectorIterator.|
|`reference`|Odwołanie do typu wewnętrznego, Platform::Collections::Details::VectorProxy\<T>,, który jest wymagany do implementacji VectorIterator.|
|`value_type`|Nazwa `T` typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Wektoryterator::Wektoriterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[WektorIterator::operator- Operator](#operator-minus)|Odejmuje określoną liczbę elementów z bieżącego iteratora, który daje nowy iterator, lub określony iterator od bieżącego iteratora, co daje liczbę elementów między iteratorami.|
|[WektorIterator::operator-- Operator](#operator-decrement)|Zmniejsza bieżący VectorIterator.|
|[WektorIterator::operator!= Operator](#operator-inequality)|Wskazuje, czy bieżący VectorIterator nie jest równy określonej vectorIterator.|
|[WektorIterator::operator* Operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżący VectorIterator.|
|[WektorIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przemieszczenie z bieżącego VectorIterator.|
|[WektorIterator::operator+ Operator](#operator-plus)|Zwraca vectorIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorIterator.|
|[WektorIterator::operator++ Operator](#operator-increment)|Zwiększa bieżącą wektoriterator.|
|[WektorIterator::operator+= Operator](#operator-plus-assign)|Zwiększa bieżący VectorIterator przez określone przemieszczenie.|
|[Wektoriterator::operator< operator](#operator-less-than)|Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.|
|[VectorIterator::operator\<= Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorIterator jest mniejszy lub równy określonej VectorIterator.|
|[WektorIterator::operator-= Operator](#operator-minus-equals)|Zmniejsza bieżący VectorIterator przez określone przemieszczenie.|
|[WektorIterator::operator== Operator](#operator-equality)|Wskazuje, czy bieżący VectorIterator jest równy określonej vectorIterator.|
|[Wektoriterator::operator> operator](#operator-greater-than)|Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.|
|[Wektoriterator::operator-operator >](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący VectorIterator.|
|[Wektoriterator::operator>= Operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorIterator jest większy lub równy określonemu VectorIteratorowi.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>WektorIterator::operator-&gt; Operator

Pobiera adres elementu, do którego odwołuje się bieżący VectorIterator.

### <a name="syntax"></a>Składnia

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego odwołuje się bieżący VectorIterator.

Typ zwracanej wartości jest nieokreślonym typem wewnętrznym, który jest wymagany do implementacji tego operatora.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>WektorIterator::operator-- Operator

Zmniejsza bieżący VectorIterator.

### <a name="syntax"></a>Składnia

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zmniejsza się, a następnie zwraca bieżący VectorIterator. Druga składnia zwraca kopię bieżącego VectorIterator, a następnie zmniejsza bieżący VectorIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorIteratora wstępnie zmniejsza bieżący VectorIterator.

Druga składnia post-decrements bieżącego VectorIterator. Typ `int` w drugiej składni wskazuje operację po dekrementacji, a nie rzeczywisty operand liczby całkowitej.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>WektorIterator::operator\*

Pobiera adres elementu określonego przez bieżący VectorIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>WektorIterator::operator== Operator

Wskazuje, czy bieżący VectorIterator jest równy określonej vectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator jest równy *innemu*; w przeciwnym razie **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>WektorIterator::operator&gt;

Wskazuje, czy bieżący VectorIterator jest większy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator jest większy niż *inne;* w przeciwnym razie **false**.

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator::operator&gt;= Operator

Wskazuje, czy bieżący VectorIterator jest większy lub równy określonemu VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator jest większy lub *równy innemu;* w przeciwnym razie **false**.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>WektorIterator::operator++ Operator

Zwiększa bieżącą wektoriterator.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżący VectorIterator. Druga składnia zwraca kopię bieżącego VectorIterator, a następnie zwiększa bieżącą VectorIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorIteratora wstępnie zwiększa bieżący VectorIterator.

Druga składnia zwiększa bieżącą wektoryteratora. Typ `int` w drugiej składni wskazuje operację przyrostową, a nie rzeczywisty argument całkowity.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>WektorIterator::operator!= Operator

Wskazuje, czy bieżący VectorIterator nie jest równy określonej vectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator nie jest równy *innym;* w przeciwnym razie **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>WektorIterator::operator&lt;

Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator jest mniejszy niż *inne;* w przeciwnym razie **false**.

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator::operator&lt;= Operator

Wskazuje, czy bieżący VectorIterator jest mniejszy lub równy określonej VectorIterator.

### <a name="syntax"></a>Składnia

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorIterator jest mniejszy lub *równy innemu;* w przeciwnym razie **false**.

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>WektorIterator::operator- Operator

Odejmuje określoną liczbę elementów z bieżącego iteratora, który daje nowy iterator, lub określony iterator od bieżącego iteratora, co daje liczbę elementów między iteratorami.

### <a name="syntax"></a>Składnia

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Szereg elementów.

*Innych*<br/>
Kolejny Wektoriterator.

### <a name="return-value"></a>Wartość zwracana

Składnia pierwszego operatora zwraca obiekt VectorIterator, który jest `n` elementami mniejszymi niż bieżący VectorIterator. Składnia drugiego operatora zwraca liczbę elementów między `other` bieżącym i VectorIterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>WektorIterator::operator+= Operator

Zwiększa bieżący VectorIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany wektoriterator.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>WektorIterator::operator+ Operator

Zwraca vectorIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorIterator.

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
W drugiej składni nazwa typu VectorIterator.

*N*<br/>
Przemieszczenie całkowite.

*I*<br/>
W drugiej składni VectorIterator.

### <a name="return-value"></a>Wartość zwracana

W pierwszej składni VectorIterator, który odwołuje się do elementu w określonym przemieszczenia z bieżącego VectorIterator.

W drugiej składni: VectorIterator, który odwołuje się do elementu przy określonym przemieszczeniu od początku parametru `i`.

### <a name="remarks"></a>Uwagi

Przykład pierwszej składni

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>WektorIterator::operator-= Operator

Zmniejsza bieżący VectorIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany wektoriterator.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>WektorIterator::operator\[\]

Pobiera odwołanie do elementu, który jest określony przemieszczenie z bieżącego VectorIterator.

### <a name="syntax"></a>Składnia

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Element, który jest `n` przesunięty przez elementy z bieżącego VectorIterator.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>Wektoryterator::Konstruktor wektorytora

Inicjuje nowe wystąpienie klasy VectorIterator.

### <a name="syntax"></a>Składnia

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Parametry

*v*<br/>
Obiekt> IVector\<T.

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni jest konstruktorem domyślnym. Drugi przykład składni jest jawnym konstruktorem, który jest używany do konstruowania\<VectorIterator z obiektu IVector T>.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
