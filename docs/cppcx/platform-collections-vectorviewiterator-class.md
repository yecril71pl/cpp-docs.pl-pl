---
title: 'Platform:: Collections:: VectorViewIterator, Klasa'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 3fed25b975eefe33f9eb7014ca91a52ba419c936
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211570"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform:: Collections:: VectorViewIterator, Klasa

Zapewnia wzorzec standardowej biblioteki szablonów dla obiektów pochodzących z `IVectorView` interfejsu środowisko wykonawcze systemu Windows.

`ViewVectorIterator`to iterator proxy, który przechowuje elementy typu `VectorProxy<T>` . Jednak obiekt proxy jest prawie nigdy niewidoczny dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Składnia

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu klasy szablonu VectorViewIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora dostępu losowego (:: std:: random_access_iterator_tag).|
|`pointer`|Wskaźnik do typu wewnętrznego, który jest wymagany dla implementacji VectorViewIterator.|
|`reference`|Odwołanie do typu wewnętrznego, który jest wymagany dla implementacji VectorViewIterator.|
|`value_type`|`T`Nazwa typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorViewIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator VectorViewIterator:: operator-](#operator-minus)|Odejmuje określoną liczbę elementów od bieżącego iteratora, który uzyskuje nowy iterator, lub określony iterator z bieżącego iteratora zwracające liczbę elementów między iteratorami.|
|[VectorViewIterator:: operator--— operator](#operator-decrement)|Zmniejsza bieżącą VectorViewIterator.|
|[Operator VectorViewIterator:: operator! =](#operator-inequality)|Wskazuje, czy bieżący VectorViewIterator nie jest równy określonemu VectorViewIterator.|
|[VectorViewIterator:: operator * — operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżącą VectorViewIterator.|
|[VectorViewIterator:: operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określonym przemieszczeniem z bieżącego VectorViewIterator.|
|[VectorViewIterator:: operator + — operator](#operator-plus)|Zwraca VectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorViewIterator.|
|[Operator VectorViewIterator:: operator + +](#operator-increment)|Zwiększa bieżącą VectorViewIterator.|
|[Operator VectorViewIterator:: operator + =](#operator-plus-equals)|Zwiększa bieżącą VectorViewIterator według określonego przemieszczenia.|
|[VectorViewIterator:: operator — operator<](#operator-less-than)|Wskazuje, czy bieżący VectorViewIterator jest mniejszy niż określony VectorViewIterator.|
|[VectorViewIterator:: operator \< = — operator](#operator-less-than-or-equals)|Wskazuje, czy bieżąca VectorViewIterator jest mniejsza lub równa określonej VectorViewIterator.|
|[Operator VectorViewIterator:: operator-=](#operator-minus-assign)|Zmniejsza bieżącą VectorViewIterator przez określone przemieszczenie.|
|[VectorViewIterator:: operator = = — operator](#operator-equality)|Wskazuje, czy bieżący VectorViewIterator jest równy określonemu VectorViewIterator.|
|[VectorViewIterator:: operator — operator>](#operator-greater-than)|Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.|
|[Operator VectorViewIterator:: operator->](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący VectorViewIterator.|
|[VectorViewIterator:: operator>= — operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest większy lub równy określonemu VectorViewIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorViewIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>Operator VectorViewIterator:: operator- &gt;

Pobiera adres elementu, do którego odwołuje się bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, do którego odwołuje się bieżąca VectorViewIterator.

Typ wartości zwracanej jest nieokreślonym typem wewnętrznym, który jest wymagany dla implementacji tego operatora.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator:: operator--— operator

Zmniejsza bieżącą VectorViewIterator.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zmniejsza się, a następnie zwraca bieżącą VectorViewIterator. Druga składnia zwraca kopię bieżącego VectorViewIterator, a następnie zmniejsza bieżącą VectorViewIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorViewIterator wstępnie zmniejsza bieżącą VectorViewIterator.

Druga składnia post — zmniejsza bieżącą VectorViewIterator. **`int`** Typ w drugiej składni wskazuje operację po zmniejszeniu, a nie rzeczywisty argument operacji całkowitej.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>Operator VectorViewIterator:: operator \*

Pobiera odwołanie do elementu określonego przez bieżącą VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator:: operator = = — operator

Wskazuje, czy bieżący VectorViewIterator jest równy określonemu VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca `VectorViewIterator` wartość jest równa *innej*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>Operator VectorViewIterator:: operator &gt;

Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.

### <a name="syntax"></a>Składnia

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący VectorViewIterator jest większy niż *inny*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator:: operator &gt; = — operator

Wskazuje, czy bieżąca `VectorViewIterator` jest większa lub równa określonej wartości `VectorViewIterator` .

### <a name="syntax"></a>Składnia

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca `VectorViewIterator` wartość jest większa lub równa *innej*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>Operator VectorViewIterator:: operator + +

Zwiększa bieżącą VectorViewIterator.

### <a name="syntax"></a>Składnia

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżącą VectorViewIterator. Druga składnia zwraca kopię bieżącego VectorViewIterator, a następnie zwiększa bieżącą VectorViewIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia VectorViewIterator wstępnie zwiększa bieżącą VectorViewIterator.

Druga składnia post-zwiększa bieżącą VectorViewIterator. **`int`** Typ w drugiej składni wskazuje operację po przyrostie, a nie rzeczywisty argument operacji całkowitej.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>Operator VectorViewIterator:: operator! =

Wskazuje, czy bieżący VectorViewIterator nie jest równy określonemu VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca `VectorViewIterator` nie jest równa *innej*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>Operator VectorViewIterator:: operator &lt;

Wskazuje, czy bieżący VectorIterator jest mniejszy niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny `VectorIterator` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca `VectorIterator` wartość jest mniejsza niż *inne*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator:: operator &lt; = — operator

Wskazuje, czy bieżące `VectorIterator` jest mniejsze niż lub równe określonej liczbie `VectorIterator` .

### <a name="syntax"></a>Składnia

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Inny `VectorIterator` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżąca `VectorIterator` wartość jest mniejsza lub równa *innej*; w przeciwnym razie **`false`** .

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>Operator VectorViewIterator:: operator-

Odejmuje określoną liczbę elementów od bieżącego iteratora, który uzyskuje nowy iterator, lub określony iterator z bieżącego iteratora zwracające liczbę elementów między iteratorami.

### <a name="syntax"></a>Składnia

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Liczba elementów.

*różnych*<br/>
Inny VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia operatora zwraca obiekt VectorViewIterator, który jest elementem `n` mniejszym od bieżącego VectorViewIterator. Druga składnia operatora zwraca liczbę elementów między bieżącą i `other` VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>Operator VectorViewIterator:: operator + =

Zwiększa bieżącą VectorViewIterator według określonego przemieszczenia.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowana VectorViewIterator.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator:: operator + — operator

Zwraca VectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z określonego VectorViewIterator.

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
W drugiej składni atrybut TypeName VectorViewIterator.

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

*i*<br/>
W drugiej składni VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

W pierwszej składni element VectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia z bieżącego VectorViewIterator.

W drugiej składni VectorViewIterator, który odwołuje się do elementu w określonym przemieszczenia od początku parametru `i` .

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>Operator VectorViewIterator:: operator-=

Zmniejsza bieżącą VectorIterator przez określone przemieszczenie.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowana VectorIterator.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator:: operator\[\]

Pobiera odwołanie do elementu, który jest określonym przemieszczeniem z bieżącego VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*Azotan*<br/>
Przemieszczenie liczb całkowitych.

### <a name="return-value"></a>Wartość zwracana

Element, który jest przemieszczenia przez `n` elementy z bieżącego VectorViewIterator.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator:: VectorViewIterator — Konstruktor

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
Obiekt IVectorView \<T> .

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni jest konstruktorem domyślnym. Drugim przykładem składni jest jawny Konstruktor, który jest używany do konstruowania elementu VectorViewIterator z \<T> obiektu IVectorView.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
