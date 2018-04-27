---
title: move_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 519da720c3dcab278a21e04baa97d1eb6e459054
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="moveiterator-class"></a>move_iterator — Klasa

Szablon klasy `move_iterator` jest otokę dla iteratora. Move_iterator zapewnia takie samo zachowanie, jak iterator, który zawija (przechowuje), z tym wyjątkiem, że zamienia operator dereferencji przechowywanego iteratora na odwołanie rvalue, zamieniając kopię na przesunięcie. Aby uzyskać więcej informacji o rvalues, zobacz [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Składnia

```cpp
class move_iterator;
```

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który zachowuje się jak iterator, z wyjątkiem przypadków, kiedy jest wyłuskiwany. Przechowuje iteratora dostępie swobodnym typu `Iterator`, używanych na funkcji członkowskiej `base()`. Wszystkie operacje na `move_iterator` są wykonywane bezpośrednio na iteratora przechowywane, z wyjątkiem tego, że wynik `operator*` niejawnie jest rzutowane na `value_type&&` dokonanie odwołania do r-wartości.

A `move_iterator` może być operacje, które nie są zdefiniowane przez opakowana iteratora. Tych operacji nie powinno się używać.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor dla obiektów typu `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iterator_type](#iterator_type)|Synonim parametru szablonu `RandomIterator`.|
|[iterator_category](#iterator_category)|Synonim dłużej `typename` wyrażenie o takiej samej nazwie `iterator_category` identyfikuje ogólne możliwości iteratora.|
|[value_type](#value_type)|Synonim dłużej `typename` wyrażenie o takiej samej nazwie `value_type` opisuje typ iteratora są elementy.|
|[difference_type](#difference_type)|Synonim dłużej `typename` wyrażenie o takiej samej nazwie `difference_type` opisuje typ całkowity wymagane wartości express różnica między elementami.|
|[pointer](#pointer)|Synonim dla parametru szablonu `RandomIterator`.|
|[Odwołanie](#reference)|Jest to synonim `rvalue` odwołania `value_type&&`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[base](#base)|Funkcja członkowska zwraca przechowywanych iteratora opakowane przez to `move_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[move_iterator::operator*](#op_star)|Zwraca `(reference)*base().`|
|[move_iterator::operator++](#op_add_add)|Inkrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja preinkrementacji, czy postinkrementacji.|
|[move_iterator::operator--](#operator--)|Dekrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja predekrementacji, czy postdekrementacji.|
|[move_iterator::operator-&gt;](#op_arrow)|Zwraca `&**this`.|
|[move_iterator::operator-](#operator-)|Zwraca `move_iterator(*this) -=` przez pierwszy odjęcie wartości po prawej stronie od bieżącego położenia.|
|[move_iterator::operator]](#op_at)|Zwraca `(reference)*(*this + off)`. Pozwala określić przesunięcie od aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+](#op_add)|Zwraca `move_iterator(*this) +=` wartość. Pozwala dodać przesunięcie do aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+=](#op_add_eq)|Dodaje wartość po prawej stronie iteratora przechowywane i zwraca `*this`.|
|[move_iterator::operator-=](#operator-_eq)|Odejmuje po prawej stronie wartości z iteratora przechowywane i zwraca `*this`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="base"></a>  move_iterator::Base

Zwraca przechowywanych iteratora tego `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywanych iteratora.

## <a name="difference_type"></a>  move_iterator::difference_type

Typ `difference_type` jest `move_iterator` `typedef` oparte na cechy iteratora `difference_type`i mogą być używane zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy iteratora `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a>  move_iterator::iterator_category

Typ `iterator_category` jest `move_iterator` `typedef` oparte na cechy iteratora `iterator_category`i mogą być używane zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy iteratora `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a>  move_iterator::iterator_type

Typ `iterator_type` opiera się na parametr szablonu `RandomIterator` dla szablonu klasy `move_iterator`i mogą być używane zamiennie w jego miejscu.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu `RandomIterator`.

## <a name="move_iterator"></a>  move_iterator::move_iterator

Tworzy iteratora przenoszenia. Parametr jako przechowywanych iteratora.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

`right` Iterator do użycia jako przechowywanych iteratora.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje przechowywanych iteratora przy użyciu jego domyślnego konstruktora. Konstruktory pozostałe inicjowanie przechowywanych iteratora z `base.base()`.

## <a name="op_add_eq"></a>  move_iterator::operator +=

Dodaje przesunięcia do iteratora przechowywane, tak, aby przechowywane iteratora wskazuje element w nowych bieżącej lokalizacji. Operator następnie przenosi nowego bieżącego elementu.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

`_Off` Przesunięcie do dodania do bieżącego położenia, aby określić nowy bieżącego położenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy bieżącego elementu.

### <a name="remarks"></a>Uwagi

Dodaje operator `_Off` do składowanej iteratora. Zwraca `*this`.

## <a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=

Przenoszenie między określoną liczbę poprzednich elementów. Ten operator odejmuje przesunięcie od przechowywanych iteratora.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator ocenia `*this += -_Off`. Zwraca `*this`.

## <a name="op_add_add"></a>  move_iterator::operator ++

Zwiększa iteratora przechowywane, który należy do tego `move_iterator.` bieżący element jest dostępny przez postincrement operatora. Następny element jest dostępny przez preincrement operatora.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy — operator (preincrement) zwiększa przechowywanych iteratora. Zwraca `*this`.

Drugi — operator (postincrement) wykonuje kopię `*this`, ocenia `++*this`. Zwraca kopię.

## <a name="op_add"></a>  move_iterator::operator +

Zwraca pozycję iteratora zaawansowane przez dowolną liczbę elementów.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a>  move_iterator::operator]

Umożliwia dostęp do indeksu tablicy do elementów w zakresie `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `(reference)*(*this + _Off)`.

## <a name="move_iterator__operator--"></a>  move_iterator::operator--

Operatorów Członkowskich przed i postdecrement wykonaj dekrementacja na przechowywanych iteratora.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy zmniejsza — operator (predecrement) elementu członkowskiego przechowywanych iteratora. Zwraca `*this`.

Drugi — operator (postdecrement) wykonuje kopię `*this`, ocenia `--*this`. Zwraca kopię.

## <a name="move_iterator__operator-"></a>  move_iterator::operator-

Zmniejsza iteratora przechowywane i zwraca określoną wartość.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) -= _Off`.

## <a name="op_star"></a>  move_iterator::operator *

Wyłuskań iteratora przechowywane i zwraca wartość. To zachowuje się jak `rvalue reference` i wykonuje przypisania przenoszenia. Operator Przenosi bieżący element poza podstawowej iteratora. Element, do którego następuje staje się nowych bieżącego elementu.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca `(reference)*base()`.

## <a name="op_arrow"></a>  move_iterator::operator-&gt;

Jako normalny, takich jak `RandomIterator` `operator->`, zapewnia dostęp do pola, które należą do bieżącego elementu.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca `&**this`.

## <a name="pointer"></a>  move_iterator::Pointer

Typ `pointer` jest `typedef` oparte na losowe iteratora `RandomIterator` dla `move_iterator`i mogą być używane zamiennie.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `RandomIterator`.

## <a name="reference"></a>  move_iterator::Reference

Typ `reference` jest `typedef` na podstawie `value_type&&` dla `move_iterator`i mogą być używane zamiennie z `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `value_type&&`, która jest odwołanie do r-wartości.

## <a name="value_type"></a>  move_iterator::value_type

Typ `value_type` jest `move_iterator` `typedef` oparte na cechy iteratora `value_type`i mogą być używane zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy iteratora `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
