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
ms.openlocfilehash: 17af246a85c4e3f1e0c7eb9d387161ad7b5123a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377409"
---
# <a name="move_iterator-class"></a>move_iterator — Klasa

Szablon `move_iterator` klasy jest otoką dla iteratora. Move_iterator zapewnia takie samo zachowanie, jak iterator, który zawija (przechowuje), z tym wyjątkiem, że zamienia operator dereferencji przechowywanego iteratora na odwołanie rvalue, zamieniając kopię na przesunięcie. Aby uzyskać więcej informacji na temat wartości r, zobacz [Rvalue Reference Declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Składnia

```cpp
class move_iterator;
```

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt, który zachowuje się jak iterator, z wyjątkiem sytuacji, gdy wyłuskane. Przechowuje iterator typu z `Iterator`dostępem losowym, dostępny `base()`za pomocą funkcji elementu członkowskiego. Wszystkie operacje `move_iterator` na są wykonywane bezpośrednio na przechowywanego iteratora, z tą różnicą, że wynik `operator*` jest niejawnie rzutowane do `value_type&&` dokonania odwołania rvalue.

A `move_iterator` może być zdolny do operacji, które nie są zdefiniowane przez opakowane iteratora. Tych operacji nie powinno się używać.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor obiektów typu `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iterator_type](#iterator_type)|Synonim parametru `RandomIterator`szablonu .|
|[Iterator_category](#iterator_category)|Synonim dłuższego wyrażenia **nazwy typu** o tej `iterator_category` samej nazwie identyfikuje ogólne zdolności iteratora.|
|[value_type](#value_type)|Synonim dłuższego wyrażenia **nazwy typu** o tej `value_type` samej nazwie opisuje, jaki typ mają elementy iteratora.|
|[difference_type](#difference_type)|Synonim dłuższego wyrażenia **nazwy typu** o tej `difference_type` samej nazwie opisuje typ całkowity wymagany do wyrażania wartości różnic między elementami.|
|[pointer](#pointer)|Synonim parametru `RandomIterator`szablonu .|
|[Odwołanie](#reference)|Synonim `rvalue` odniesienia `value_type&&`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[base](#base)|Funkcja elementu członkowskiego zwraca przechowywany iterator zawinięty przez ten `move_iterator`plik .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[move_iterator::operator*](#op_star)|Zwraca`(reference)*base().`|
|[move_iterator::operator++](#op_add_add)|Inkrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja preinkrementacji, czy postinkrementacji.|
|[move_iterator::operator--](#operator--)|Dekrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja predekrementacji, czy postdekrementacji.|
|[move_iterator::operator-&gt;](#op_arrow)|Zwraca wartość `&**this`.|
|[move_iterator::operator-](#operator-)|Zwraca `move_iterator(*this) -=` najpierw wartość po prawej stronie od bieżącej pozycji.|
|[move_iterator::operator[]](#op_at)|Zwraca wartość `(reference)*(*this + off)`. Pozwala określić przesunięcie od aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+](#op_add)|Zwraca `move_iterator(*this) +=` wartość. Pozwala dodać przesunięcie do aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+=](#op_add_eq)|Dodaje wartość po prawej stronie do przechowywanego `*this`iteratora i zwraca .|
|[move_iterator::operator-=](#operator-_eq)|Odejmuje wartość po prawej stronie od przechowywanego `*this`iteratora i zwraca .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="move_iteratorbase"></a><a name="base"></a>move_iterator::base

Zwraca dla tego zapisanego `move_iterator`iteratora .

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywany iterator.

## <a name="move_iteratordifference_type"></a><a name="difference_type"></a>move_iterator::d00_typ

Typ `difference_type` jest `move_iterator` `typedef` oparty na traty `difference_type`iteratora i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy `typename iterator_traits<RandomIterator>::pointer`iteratora .

## <a name="move_iteratoriterator_category"></a><a name="iterator_category"></a>move_iterator::iterator_category

Typ `iterator_category` jest `move_iterator` `typedef` oparty na traty `iterator_category`iteratora i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy `typename iterator_traits<RandomIterator>::iterator_category`iteratora .

## <a name="move_iteratoriterator_type"></a><a name="iterator_type"></a>move_iterator::iterator_type

Typ `iterator_type` jest oparty na `RandomIterator` parametrze szablonu dla szablonu `move_iterator`klasy i może być używany zamiennie w jego miejscu.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `RandomIterator`szablonu .

## <a name="move_iteratormove_iterator"></a><a name="move_iterator"></a>move_iterator::move_iterator

Konstruuje iteratora przenoszenia. Używa parametru jako przechowywanego iteratora.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator do użycia jako przechowywane iteratora.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje przechowywane iterator z jego domyślnego konstruktora. Pozostałe konstruktory inicjują `base.base()`przechowywany iterator za pomocą pliku .

## <a name="move_iteratoroperator"></a><a name="op_add_eq"></a>move_iterator::operator+=

Dodaje przesunięcie do przechowywanego iteratora, dzięki czemu przechowywany iterator wskazuje na element w nowej bieżącej lokalizacji. Operator następnie przenosi nowy bieżący element.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, aby dodać do bieżącej pozycji, aby określić nową pozycję bieżącą.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy bieżący element.

### <a name="remarks"></a>Uwagi

Operator dodaje *_Off* do przechowywanego iteratora. Następnie `*this`zwraca plik .

## <a name="move_iteratoroperator-"></a><a name="operator-_eq"></a>move_iterator::operator-=

Porusza się po określonej liczbie poprzednich elementów. Ten operator odejmuje przesunięcie od przechowywanego iteratora.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator ocenia `*this += -_Off`. Następnie `*this`zwraca plik .

## <a name="move_iteratoroperator"></a><a name="op_add_add"></a>move_iterator::operator++

Przyrosty przechowywane iteratora, który `move_iterator.` należy do tego bieżącego elementu jest dostępny przez operatora postincrement. Operator preincrement uzyskiwał dostęp do następnego elementu.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy operator (preincrement) zwiększa przechowywany iterator. Następnie `*this`zwraca plik .

Drugi operator (postincrement) tworzy `*this`kopię , `++*this`ocenia . Następnie zwraca kopię.

## <a name="move_iteratoroperator"></a><a name="op_add"></a>move_iterator::operator+

Zwraca pozycję iteratora zaawansowane przez dowolną liczbę elementów.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) +=` `_Off`.

## <a name="move_iteratoroperator"></a><a name="op_at"></a>move_iterator::operator[]

Umożliwia dostęp do indeksu tablicy `move iterator`do elementów w całym zakresie .

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `(reference)*(*this + _Off)`.

## <a name="move_iteratoroperator--"></a><a name="operator--"></a>move_iterator::operator--

Operatory członkowskie przed i po zakończeniu tworzenia kroków wykonują dekrementowanie na przechowywanym iteratorze.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy operator elementu członkowskiego (predecrement) zmniejsza przechowywane iteratora. Następnie `*this`zwraca plik .

Drugi operator (postdecrement) tworzy `*this`kopię , `--*this`ocenia . Następnie zwraca kopię.

## <a name="move_iteratoroperator-"></a><a name="operator-"></a>move_iterator::operator-

Zmniejsza przechowywany iterator i zwraca wskazaną wartość.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) -= _Off`.

## <a name="move_iteratoroperator"></a><a name="op_star"></a>move_iterator::operator*

Wyłudy za przechowywany iterator i zwraca wartość. Zachowuje się to `rvalue reference` jak i wykonuje przypisanie przenoszenia. Operator przenosi bieżący element z podstawowego iteratora. Element, który następuje staje się nowym bieżącym elementem.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca `(reference)*base()`.

## <a name="move_iteratoroperator-gt"></a><a name="op_arrow"></a>move_iterator::operator-&gt;

Podobnie jak `RandomIterator` `operator->`normalny , zapewnia dostęp do pól, które należą do bieżącego elementu.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Uwagi

Operator zwraca `&**this`.

## <a name="move_iteratorpointer"></a><a name="pointer"></a>move_iterator::pointer

Typ `pointer` jest **typedef** na podstawie losowego `RandomIterator` `move_iterator`iteratora dla , i może być używany zamiennie.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `RandomIterator`.

## <a name="move_iteratorreference"></a><a name="reference"></a>move_iterator::odwołanie

Typ `reference` jest **typedef** na `value_type&&` `move_iterator`podstawie , i może `value_type&&`być używany zamiennie z .

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `value_type&&`, który jest odwołaniem rvalue.

## <a name="move_iteratorvalue_type"></a><a name="value_type"></a>move_iterator::value_type

Typ `value_type` jest `move_iterator` `typedef` oparty na traty `value_type`iteratora i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem cechy `typename iterator_traits<RandomIterator>::value_type`iteratora .

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Wartości lvalues i wartości r](../cpp/lvalues-and-rvalues-visual-cpp.md)\
[Przenoszenie konstruktorów i operatorów przenoszenia przydziałów (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
