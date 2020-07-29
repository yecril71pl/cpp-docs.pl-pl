---
title: move_iterator — Klasa
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 55e0c23aaf085a132ecab739ec1d4ff1f11858a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228196"
---
# <a name="move_iterator-class"></a>move_iterator — Klasa

Szablon klasy `move_iterator` jest otoką dla iteratora. Move_iterator zapewnia takie samo zachowanie, jak iterator, który zawija (przechowuje), z tym wyjątkiem, że zamienia operator dereferencji przechowywanego iteratora na odwołanie rvalue, zamieniając kopię na przesunięcie. Aby uzyskać więcej informacji na temat rvalues, zobacz [rvalue Reference deklarator:  &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Składnia

```cpp
class move_iterator;
```

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który zachowuje się jak iterator, z wyjątkiem sytuacji, gdy jest wykorzystana. Zapisuje Iterator dostępu swobodnego typu `Iterator` , do którego można uzyskać dostęp za pomocą funkcji składowej `base()` . Wszystkie operacje na a `move_iterator` są wykonywane bezpośrednio na zapisywanym iteratorze, z tą różnicą, że wynik elementu `operator*` jest niejawnie rzutowany na, `value_type&&` Aby utworzyć odwołanie rvalue.

`move_iterator`Mogą być możliwe operacje, które nie są zdefiniowane przez iterator opakowany. Tych operacji nie powinno się używać.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor dla obiektów typu `move_iterator` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iterator_type](#iterator_type)|Synonim dla parametru szablonu `RandomIterator` .|
|[iterator_category](#iterator_category)|Synonim o dłuższym **`typename`** wyrażeniu o tej samej nazwie `iterator_category` określa ogólne możliwości iteratora.|
|[value_type](#value_type)|Synonim o dłuższym **`typename`** wyrażeniu o tej samej nazwie, który `value_type` opisuje typ elementów iteratora.|
|[difference_type](#difference_type)|Synonim o dłuższym **`typename`** wyrażeniu o tej samej nazwie `difference_type` zawiera opis typu całkowitego wymaganego do wyrażenia wartości różnic między elementami.|
|[pointer](#pointer)|Synonim dla parametru szablonu `RandomIterator` .|
|[odwoła](#reference)|Synonim dla `rvalue` odwołania `value_type&&` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[base](#base)|Funkcja członkowska zwraca zapisany iterator opakowany w ten sposób `move_iterator` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[move_iterator:: operator *](#op_star)|Typu`(reference)*base().`|
|[move_iterator:: operator + +](#op_add_add)|Inkrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja preinkrementacji, czy postinkrementacji.|
|[move_iterator:: operator--](#operator--)|Dekrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja predekrementacji, czy postdekrementacji.|
|[move_iterator:: operator-&gt;](#op_arrow)|Zwraca wartość `&**this`.|
|[move_iterator:: operator-](#operator-)|Zwraca `move_iterator(*this) -=` przez pierwsze odjęcie wartości z prawej strony od bieżącego położenia.|
|[move_iterator:: operator []](#op_at)|Zwraca wartość `(reference)*(*this + off)`. Pozwala określić przesunięcie od aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator:: operator +](#op_add)|Zwraca `move_iterator(*this) +=` wartość. Pozwala dodać przesunięcie do aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator:: operator + =](#op_add_eq)|Dodaje wartość z prawej strony do przechowywanego iteratora i zwraca **`*this`** .|
|[move_iterator:: operator-=](#operator-_eq)|Odejmuje wartość z prawej strony od przechowywanego iteratora i zwraca **`*this`** .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<iterator>

**Przestrzeń nazw:** std

## <a name="move_iteratorbase"></a><a name="base"></a>move_iterator:: Base

Zwraca zapisany iterator dla tego elementu `move_iterator` .

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany iterator.

## <a name="move_iteratordifference_type"></a><a name="difference_type"></a>move_iterator::d ifference_type

Typ `difference_type` jest `move_iterator` **`typedef`** oparty na charakterystyce iteratora `difference_type` i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::pointer` .

## <a name="move_iteratoriterator_category"></a><a name="iterator_category"></a>move_iterator:: iterator_category

Typ `iterator_category` jest `move_iterator` **`typedef`** oparty na charakterystyce iteratora `iterator_category` i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::iterator_category` .

## <a name="move_iteratoriterator_type"></a><a name="iterator_type"></a>move_iterator:: iterator_type

Typ `iterator_type` jest oparty na parametrze szablonu `RandomIterator` dla szablonu klasy `move_iterator` i może być używany zamiennie w jego miejsce.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `RandomIterator` .

## <a name="move_iteratormove_iterator"></a><a name="move_iterator"></a>move_iterator:: move_iterator

Konstruuje iterator przenoszenia. Używa parametru jako iteratora przechowywanego.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Iterator, który ma być używany jako iterator przechowywany.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje przechowywany iterator przy użyciu domyślnego konstruktora. Pozostałe konstruktory inicjują przechowywany iterator przy użyciu `base.base()` .

## <a name="move_iteratoroperator"></a><a name="op_add_eq"></a>move_iterator:: operator + =

Dodaje przesunięcie do przechowywanego iteratora, tak aby zapisane iterator wskazywały element w nowej lokalizacji. Następnie operator przenosi nowy bieżący element.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, które ma zostać dodane do bieżącego położenia, aby określić nowe bieżące położenie.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy element Current.

### <a name="remarks"></a>Uwagi

Operator dodaje *_Off* do przechowywanego iteratora. Następnie zwraca wartość **`*this`** .

## <a name="move_iteratoroperator-"></a><a name="operator-_eq"></a>move_iterator:: operator-=

Przenosi przez określoną liczbę poprzednich elementów. Ten operator odejmuje przesunięcie od przechowywanego iteratora.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator oblicza `*this += -_Off` . Następnie zwraca wartość **`*this`** .

## <a name="move_iteratoroperator"></a><a name="op_add_add"></a>move_iterator:: operator + +

Zwiększa składowany iterator, który należy do bieżącego elementu, do którego `move_iterator.` uzyskuje dostęp operator postinkrementacji. Do następnego elementu uzyskuje się dostęp za pomocą operatora przedrastania.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy (przyrostowy) operator zwiększa przechowywany iterator. Następnie zwraca wartość **`*this`** .

Drugi operator (postinkrementacji) wykonuje kopię **`*this`** , szacuje `++*this` . Następnie zwraca kopię.

## <a name="move_iteratoroperator"></a><a name="op_add"></a>move_iterator:: operator +

Zwraca pozycję iteratora zaawansowaną przez dowolną liczbę elementów.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca wartość `move_iterator(*this) +=` `_Off` .

## <a name="move_iteratoroperator"></a><a name="op_at"></a>move_iterator:: operator []

Umożliwia indeksowi tablicy dostęp do elementów w zakresie `move iterator` .

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca wartość `(reference)*(*this + _Off)` .

## <a name="move_iteratoroperator--"></a><a name="operator--"></a>move_iterator:: operator--

Operatory składowe pre-i postdekrementacyjne wykonują zmniejszenie zapisywanych iteratorów.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu członkowskiego (zmniejszający) zmniejsza przechowywany iterator. Następnie zwraca wartość **`*this`** .

Drugi operator (postdekrementacyjne) wykonuje kopię **`*this`** , szacuje `--*this` . Następnie zwraca kopię.

## <a name="move_iteratoroperator-"></a><a name="operator-"></a>move_iterator:: operator-

Zmniejsza składowany iterator i zwraca określoną wartość.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca wartość `move_iterator(*this) -= _Off` .

## <a name="move_iteratoroperator"></a><a name="op_star"></a>move_iterator:: operator *

Odwołuje się do przechowywanego iteratora i zwraca wartość. Zachowuje się to jak `rvalue reference` i wykonuje przypisanie przenoszenia. Operator przenosi bieżący element z iteratora podstawowego. Poniższy element jest nowym bieżącym elementem.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość `(reference)*base()` .

## <a name="move_iteratoroperator-gt"></a><a name="op_arrow"></a>move_iterator:: operator-&gt;

Podobnie jak w przypadku normalnego `RandomIterator` `operator->` , zapewnia dostęp do pól, które należą do bieżącego elementu.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca wartość `&**this` .

## <a name="move_iteratorpointer"></a><a name="pointer"></a>move_iterator::p ointer

Typ `pointer` jest **`typedef`** oparty na iteratorie losowym `RandomIterator` dla `move_iterator` i może być używany zamiennie.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `RandomIterator` .

## <a name="move_iteratorreference"></a><a name="reference"></a>move_iterator:: Reference

Typ `reference` jest **`typedef`** oparty na `value_type&&` dla `move_iterator` i może być używany zamiennie z `value_type&&` .

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type&&` , który jest odwołaniem rvalue.

## <a name="move_iteratorvalue_type"></a><a name="value_type"></a>move_iterator:: value_type

Typ `value_type` jest `move_iterator` **`typedef`** oparty na charakterystyce iteratora `value_type` i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::value_type` .

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[Przenieś konstruktory i operatory przypisania przenoszenia (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
