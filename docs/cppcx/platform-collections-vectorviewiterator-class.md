---
title: 'Platform::Collections:: vectorviewiterator, klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 6ee03b546cf89aff3ef79fa9c89d15f39b4d9fe0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539142"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections:: vectorviewiterator, klasa

Dostarcza iterator standardowej biblioteki szablonów dla obiektów pochodzących od środowiska uruchomieniowego Windows`IVectorView` interfejsu.

`ViewVectorIterator` jest iteratorem serwera proxy, który przechowuje elementy typu `VectorProxy<T>`. Jednak obiekt serwera proxy prawie nigdy nie jest widoczne dla kodu użytkownika. Aby uzyskać więcej informacji, zobacz [kolekcje (C + +/ CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Składnia

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Element typename VectorViewIterator szablonu klasy.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźników przy obliczaniu (ptrdiff_t —).|
|`iterator_category`|Kategoria iteratora dostępu swobodnego (:: std::random_access_iterator_tag).|
|`pointer`|Wskaźnik do typu wewnętrznego, który jest wymagany do wykonania VectorViewIterator.|
|`reference`|Odwołanie do typu wewnętrznego, który jest wymagany do wykonania VectorViewIterator.|
|`value_type`|`T` Typename.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicjuje nowe wystąpienie klasy VectorViewIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[VectorViewIterator::operator-— Operator](#operator-minus)|Odejmuje określoną liczbę elementów z bieżącego iteratora reaguje iterator nowych lub określony iteratora z bieżącego iteratora reaguje liczbę elementów między Iteratory.|
|[VectorViewIterator::operator — Operator](#operator-decrement)|Zmniejsza bieżące VectorViewIterator.|
|[VectorViewIterator::operator! = — Operator](#operator-inequality)|Wskazuje, czy bieżący VectorViewIterator nie jest równa określonej VectorViewIterator.|
|[VectorViewIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżący VectorViewIterator.|
|[VectorViewIterator::operator\[\]](#operator-at)|Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorViewIterator.|
|[VectorViewIterator::operator + — Operator](#operator-plus)|Zwraca VectorViewIterator, która odwołuje się do elementu w określonym przemieszczenia VectorViewIterator określony.|
|[VectorViewIterator::operator ++ — Operator](#operator-increment)|Zwiększa narastająco VectorViewIterator bieżącego.|
|[VectorViewIterator::operator += — Operator](#operator-plus-assign)|Zwiększa bieżącego VectorViewIterator o określonym przemieszczenia.|
|[VectorViewIterator::operator < — Operator](#operator-less-than)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza niż określony VectorViewIterator.|
|[VectorViewIterator::operator\<= — Operator](#operator-less-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest mniejsza niż lub równa określonej VectorViewIterator.|
|[VectorViewIterator::operator-= — Operator](#operator-minus-assign)|Zmniejsza bieżące VectorViewIterator przemieszczenie określony.|
|[VectorViewIterator::operator == — Operator](#operator-equality)|Wskazuje, czy bieżący VectorViewIterator jest równe określonej VectorViewIterator.|
|[VectorViewIterator::operator > — Operator](#operator-greater-than)|Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.|
|[VectorViewIterator::operator -> — Operator](#operator-arrow)|Pobiera adres elementu przywoływane przez bieżący VectorViewIterator.|
|[VectorViewIterator::operator > = — Operator](#operator-greater-than-or-equals)|Wskazuje, czy bieżący VectorViewIterator jest większa niż lub równa określonej VectorViewIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VectorViewIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

## <a name="operator-arrow"></a>  VectorViewIterator::operator -&gt; — Operator

Pobiera adres elementu przywoływane przez bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu, który odwołuje się do bieżącego VectorViewIterator.

Typ wartości zwracanej jest nieokreślonego typu wewnętrznego, który jest wymagany do wykonania tego operatora.

## <a name="operator-decrement"></a>  VectorViewIterator::operator — Operator

Zmniejsza bieżące VectorViewIterator.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy zmniejsza składni, a następnie zwraca bieżący VectorViewIterator. Składnia drugiego zwraca kopię bieżącego VectorViewIterator, a następnie zmniejsza VectorViewIterator bieżącego.

### <a name="remarks"></a>Uwagi

Pierwszy składni VectorViewIterator decrements wstępnie VectorViewIterator bieżącego.

Składnia drugiego decrements po bieżącym VectorViewIterator. `int` Typu w drugim składni wskazuje to operacja dekrementacji po nie operandu rzeczywistej liczby całkowitej.

## <a name="operator-dereference"></a>  VectorViewIterator::operator\* — Operator

Pobiera odwołanie do elementu określonego przez bieżący VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący VectorViewIterator.

## <a name="operator-equality"></a>  VectorViewIterator::operator == — Operator

Wskazuje, czy bieżący VectorViewIterator jest równe określonej VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
VectorViewIterator innego.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `VectorViewIterator` jest równa *innych*; w przeciwnym razie **false**.

## <a name="operator-greater-than"></a>  VectorViewIterator::operator&gt; — Operator

Wskazuje, czy bieżący VectorViewIterator jest większy niż określony VectorViewIterator.

### <a name="syntax"></a>Składnia

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
VectorViewIterator innego.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące VectorViewIterator jest większa niż *innych*; w przeciwnym razie **false**.

## <a name="operator-greater-than-or-equals"></a>  VectorViewIterator::operator&gt;= — Operator

Wskazuje, czy bieżący `VectorViewIterator` jest większa niż lub równa określonej `VectorViewIterator`.

### <a name="syntax"></a>Składnia

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
VectorViewIterator innego.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `VectorViewIterator` jest większa niż lub równa *innych*; w przeciwnym razie **false**.

## <a name="operator-increment"></a>  VectorViewIterator::operator ++ — Operator

Zwiększa narastająco VectorViewIterator bieżącego.

### <a name="syntax"></a>Składnia

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy składni zwiększa, a następnie zwraca bieżący VectorViewIterator. Drugiej składni zwraca kopię bieżącego VectorViewIterator, a następnie zwiększa VectorViewIterator bieżącego.

### <a name="remarks"></a>Uwagi

Pierwszy składni VectorViewIterator zwiększa wstępnie VectorViewIterator bieżącego.

Składnia drugiego zwiększa po bieżącym VectorViewIterator. `int` Typu w drugim składni wskazuje operacji po inkrementacji, nie operandu rzeczywistej liczby całkowitej.

## <a name="operator-inequality"></a>  VectorViewIterator::operator! = — Operator

Wskazuje, czy bieżący VectorViewIterator nie jest równa określonej VectorViewIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
VectorViewIterator innego.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `VectorViewIterator` nie jest równa *innych*; w przeciwnym razie **false**.

## <a name="operator-less-than"></a>  VectorViewIterator::operator&lt; — Operator

Wskazuje, czy bieżący VectorIterator jest mniejsza niż określony VectorIterator.

### <a name="syntax"></a>Składnia

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
Inny `VectorIterator`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `VectorIterator` jest mniejsza niż *innych*; w przeciwnym razie **false**.

## <a name="operator-less-than-or-equals"></a>  VectorViewIterator::operator&lt;= — Operator

Wskazuje, czy bieżący `VectorIterator` jest mniejsza lub równa określonej `VectorIterator`.

### <a name="syntax"></a>Składnia

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*other*<br/>
Inny `VectorIterator`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bieżące `VectorIterator` jest mniejsza niż lub równa *innych*; w przeciwnym razie **false**.

## <a name="operator-minus"></a>  VectorViewIterator::operator-— Operator

Odejmuje określoną liczbę elementów z bieżącego iteratora reaguje iterator nowych lub określony iteratora z bieżącego iteratora reaguje liczbę elementów między Iteratory.

### <a name="syntax"></a>Składnia

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Liczba elementów.

*other*<br/>
VectorViewIterator innego.

### <a name="return-value"></a>Wartość zwracana

Pierwszy składnia operator zwraca obiekt VectorViewIterator `n` elementy mniejszą niż bieżący VectorViewIterator. Drugi składni operator zwraca liczbę elementów między bieżącą i `other` VectorViewIterator.

## <a name="operator-plus-equals"></a>  VectorViewIterator::operator += — Operator

Zwiększa bieżącego VectorViewIterator o określonym przemieszczenia.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przesunięcie liczby całkowitej.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowano VectorViewIterator.

## <a name="operator-plus"></a>  VectorViewIterator::operator + — Operator

Zwraca VectorViewIterator, która odwołuje się do elementu w określonym przemieszczenia VectorViewIterator określony.

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
W drugim składnia elementu VectorViewIterator typename.

*N*<br/>
Przesunięcie liczby całkowitej.

*i*<br/>
W drugim składni VectorViewIterator.

### <a name="return-value"></a>Wartość zwracana

W pierwszym składni VectorViewIterator, która odwołuje się do elementu w określonym przemieszczenia VectorViewIterator bieżącego.

W drugim składni VectorViewIterator, który odwołuje się do elementu w określonej przesunięcie od początku parametru `i`.

## <a name="operator-minus-assign"></a>  VectorViewIterator::operator-= — Operator

Zmniejsza bieżące VectorIterator przemieszczenie określony.

### <a name="syntax"></a>Składnia

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przesunięcie liczby całkowitej.

### <a name="return-value"></a>Wartość zwracana

Zaktualizowano VectorIterator.

## <a name="operator-at"></a>  VectorViewIterator::operator\[\]

Pobiera odwołanie do elementu, który jest określony przesunięcia z bieżącej VectorViewIterator.

### <a name="syntax"></a>Składnia

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parametry

*N*<br/>
Przesunięcie liczby całkowitej.

### <a name="return-value"></a>Wartość zwracana

Element, który jest przesunięty przez `n` elementy z bieżącego VectorViewIterator.

## <a name="ctor"></a>  Konstruktor VectorViewIterator::VectorViewIterator

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
IVectorView\<T > obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni jest konstruktor domyślny. Drugi przykład składni jest jawny Konstruktor, który służy do konstruowania VectorViewIterator z IVectorView\<T > obiektu.

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)