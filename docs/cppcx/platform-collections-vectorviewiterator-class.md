---
title: Platform::Collections::VectorViewIterator, klasa
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363695"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator, klasa

Udostępnia iterator biblioteki szablonów standardowych dla obiektów`IVectorView` pochodzących z interfejsu środowiska wykonawczego systemu Windows.

`ViewVectorIterator`jest iteratorem proxy, który `VectorProxy<T>`przechowuje elementy typu . Jednak obiekt proxy prawie nigdy nie jest widoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [Kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Składnia

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu klasy szablonu VectorViewIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora dostępu losowego (::std::random_access_iterator_tag).|
|`pointer`|Wskaźnik do typu wewnętrznego, który jest wymagany do implementacji VectorViewIterator.|
|`reference`|Odwołanie do typu wewnętrznego, który jest wymagany do implementacji VectorViewIterator.|
|`value_type`|Nazwa `T` typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorViewIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorViewIterator::operator- Operator](#operator-minus)|Odejmuje określoną liczbę elementów z bieżącego iteratora, który daje nowy iterator, lub określony iterator od bieżącego iteratora, co daje liczbę elementów między iteratorami.|
|[VectorViewIterator::operator-- Operator](#operator-decrement)|Zmniejsza bieżący VectorViewIterator.|
|[VectorViewIterator::operator!= Operator](#operator-inequality)|Wskazuje, czy bieżący VectorViewIterator nie jest równy określonej VectorViewIterator.|
|[VectorViewIterator::operator* Operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżący VectorViewIterator.|
|[VectorViewIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przemieszczenie z bieżącego VectorViewIterator.|
|[VectorViewIterator::operator+ Operator](#operator-plus)|Zwraca vectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorViewIterator.|
|[VectorViewIterator::operator++ Operator](#operator-increment)|Zwiększa bieżącą VectorViewIterator.|
|[VectorViewIterator::operator+= Operator](#operator-plus-equals)|Zwiększa bieżący VectorViewIterator przez określone przemieszczenie.|
|[VectorViewIterator::operator< Operator](#operator-less-than)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza niż określony VectorViewIterator.|
|[VectorViewIterator::operator\<= Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza lub równa określonej VectorViewIterator.|
|[VectorViewIterator::operator-= Operator](#operator-minus-assign)|Zmniejsza bieżący VectorViewIterator przez określone przemieszczenie.|
|[VectorViewIterator::operator== Operator](#operator-equality)|Wskazuje, czy bieżący VectorViewIterator jest równy określonej VectorViewIterator.|
|[VectorViewIterator::operator> Operator](#operator-greater-than)|Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.|
|[WektorViewIterator::operator-operator >](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący VectorViewIterator.|
|[VectorViewIterator::operator>= Operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest większa lub równa określonej VectorViewIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorViewIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator::operator-&gt; Operator

Pobiera adres elementu, do którego odwołuje się bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego odwołuje się bieżący VectorViewIterator.

Typ zwracanej wartości jest nieokreślonym typem wewnętrznym, który jest wymagany do implementacji tego operatora.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator::operator-- Operator

Zmniejsza bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zmniejsza się, a następnie zwraca bieżący VectorViewIterator. Druga składnia zwraca kopię bieżącego VectorViewIterator, a następnie zmniejsza bieżący VectorViewIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorViewIterator wstępnie zmniejsza bieżący VectorViewIterator.

Druga składnia post-decrements bieżącego VectorViewIterator. Typ `int` w drugiej składni wskazuje operację po dekrementacji, a nie rzeczywisty operand liczby całkowitej.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator::operator\* operatora

Pobiera odwołanie do elementu określonego przez bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator::operator== Operator

Wskazuje, czy bieżący VectorViewIterator jest równy określonej VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `VectorViewIterator` prąd jest równy *innemu;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator::operator&gt; operatora

Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.

### <a name="syntax"></a>Składnia

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący VectorViewIterator jest większy niż *inne;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator::operator&gt;= Operator

Wskazuje, czy `VectorViewIterator` prąd jest większy lub `VectorViewIterator`równy określonemu .

### <a name="syntax"></a>Składnia

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeżeli `VectorViewIterator` prąd jest większy lub równy *innemu;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator::operator++ Operator

Zwiększa bieżącą VectorViewIterator.

### <a name="syntax"></a>Składnia

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżący VectorViewIterator. Druga składnia zwraca kopię bieżącego VectorViewIterator, a następnie zwiększa bieżący VectorViewIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorViewIterator wstępnie zwiększa bieżący VectorViewIterator.

Druga składnia zwiększa przyrost bieżącej VectorViewIterator. Typ `int` w drugiej składni wskazuje operację przyrostową, a nie rzeczywisty argument całkowity.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>VectorViewIterator::operator!= Operator

Wskazuje, czy bieżący VectorViewIterator nie jest równy określonej VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `VectorViewIterator` prąd nie jest równy *innemu;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator::operator&lt; operatora

Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny `VectorIterator`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `VectorIterator` prąd jest mniejszy niż *inny;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator::operator&lt;= Operator

Wskazuje, czy `VectorIterator` prąd jest mniejszy lub `VectorIterator`równy określonej .

### <a name="syntax"></a>Składnia

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Kolejny `VectorIterator`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeżeli `VectorIterator` prąd jest mniejszy lub równy *innemu;* w przeciwnym razie **false**.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator::operator- Operator

Odejmuje określoną liczbę elementów z bieżącego iteratora, który daje nowy iterator, lub określony iterator od bieżącego iteratora, co daje liczbę elementów między iteratorami.

### <a name="syntax"></a>Składnia

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Szereg elementów.

*Innych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia operatora zwraca VectorViewIterator obiektu, który jest `n` elementy mniejsze niż bieżący VectorViewIterator. Składnia drugiego operatora zwraca liczbę elementów między `other` bieżącym i VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>VectorViewIterator::operator+= Operator

Zwiększa bieżący VectorViewIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany VectorViewiterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator::operator+ Operator

Zwraca vectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorViewIterator.

### <a name="syntax"></a>Składnia

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parametry

*T*<br/>
W drugiej składni nazwa typu VectorViewIterator.

*N*<br/>
Przemieszczenie całkowite.

*I*<br/>
W drugiej składni VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

W pierwszej składni VectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z bieżącego VectorViewIterator.

W drugiej składni: VectorViewIterator, który odwołuje się do elementu przy określonym przemieszczeniu od początku parametru `i`.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>VectorViewIterator::operator-= Operator

Zmniejsza bieżący VectorIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowany wektoriterator.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator::operator\[\]

Pobiera odwołanie do elementu, który jest określony przemieszczenie z bieżącego VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przemieszczenie całkowite.

### <a name="return-value"></a>Wartość zwracana

Element, który jest `n` przesunięty przez elementy z bieżącego VectorViewIterator.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator::VectorViewIterator Konstruktor

Inicjuje nowe wystąpienie klasy VectorViewIterator.

### <a name="syntax"></a>Składnia

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parametry

*v*<br/>
Obiekt> IVectorView\<T.

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni jest konstruktorem domyślnym. Drugi przykład składni jest jawnym konstruktorem, który jest używany do konstruowania VectorViewIterator z obiektu> IVectorView\<T.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
