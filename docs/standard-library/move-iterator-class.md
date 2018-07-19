---
title: move_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4dfbd3bc6a020dba4b6e5eb868e21ec37fcc1ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955250"
---
# <a name="moveiterator-class"></a>move_iterator — Klasa

Szablon klasy `move_iterator` jest otoką dla iteratora. Move_iterator zapewnia takie samo zachowanie, jak iterator, który zawija (przechowuje), z tym wyjątkiem, że zamienia operator dereferencji przechowywanego iteratora na odwołanie rvalue, zamieniając kopię na przesunięcie. Aby uzyskać więcej informacji o rvalue, zobacz [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Składnia

```cpp
class move_iterator;
```

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który zachowuje się jak iterator, z wyjątkiem przypadków, kiedy jest wyłuskiwany. Przechowuje iterator dostępu swobodnego typu `Iterator`, do których uzyskano dostęp za pomocą funkcji elementu członkowskiego `base()`. Wszystkie operacje na `move_iterator` są wykonywane bezpośrednio na przechowywanym iteratorze, z tą różnicą, że wynik `operator*` jest niejawnie rzutowany na `value_type&&` się odwołanie rvalue.

Element `move_iterator` może być zdolny do operacji, które nie są zdefiniowane przez zawinięty iterator. Tych operacji nie powinno się używać.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[move_iterator](#move_iterator)|Konstruktor dla obiektów typu `move_iterator`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[iterator_type](#iterator_type)|Synonim dla parametru szablonu `RandomIterator`.|
|[iterator_category](#iterator_category)|Synonim dla dłuższego **typename** wyrażenie o takiej samej nazwie `iterator_category` określa ogólne możliwości iteratora.|
|[value_type](#value_type)|Synonim dla dłuższego **typename** wyrażenie o takiej samej nazwie `value_type` opisuje typ elementów iteratora.|
|[difference_type](#difference_type)|Synonim dla dłuższego **typename** wyrażenie o takiej samej nazwie `difference_type` opisuje typ całkowitoliczbowy wymagany do wartości różnicy między elementami.|
|[pointer](#pointer)|Synonim dla parametru szablonu `RandomIterator`.|
|[Odwołanie](#reference)|Synonim dla `rvalue` odwołania `value_type&&`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[base](#base)|Funkcja elementu członkowskiego zwraca przechowywany iterator owinięty przez ten `move_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[move_iterator::operator*](#op_star)|Zwraca `(reference)*base().`|
|[move_iterator::operator++](#op_add_add)|Inkrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja preinkrementacji, czy postinkrementacji.|
|[move_iterator::operator--](#operator--)|Dekrementuje przechowywany iterator. Dokładne zachowanie zależy od tego, czy jest to operacja predekrementacji, czy postdekrementacji.|
|[move_iterator::operator-&gt;](#op_arrow)|Zwraca `&**this`.|
|[move_iterator::operator-](#operator-)|Zwraca `move_iterator(*this) -=` przez odjęcie najpierw wartości po prawej stronie od bieżącej pozycji.|
|[move_iterator::operator]](#op_at)|Zwraca `(reference)*(*this + off)`. Pozwala określić przesunięcie od aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+](#op_add)|Zwraca `move_iterator(*this) +=` wartość. Pozwala dodać przesunięcie do aktualnej podstawy, aby uzyskać wartość w tej lokalizacji.|
|[move_iterator::operator+=](#op_add_eq)|Dodaje wartości po prawej stronie przechowywanego iteratora i zwraca `*this`.|
|[move_iterator::operator-=](#operator-_eq)|Odejmuje wartość po prawej stronie od przechowywanego iteratora i zwraca `*this`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="base"></a>  move_iterator::Base

Zwraca przechowywany iterator dla tego `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywany iterator.

## <a name="difference_type"></a>  move_iterator::difference_type

Typ `difference_type` jest `move_iterator` `typedef` oparte na cech iteratora `difference_type`i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a>  move_iterator::iterator_category

Typ `iterator_category` jest `move_iterator` `typedef` oparte na cech iteratora `iterator_category`i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a>  move_iterator::iterator_type

Typ `iterator_type` zależy od parametru szablonu `RandomIterator` dla szablonu klasy `move_iterator`i mogą być używane zamiennie w tym miejscu.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `RandomIterator`.

## <a name="move_iterator"></a>  move_iterator::move_iterator

Tworzy iterator przenoszenia. Parametr jako przechowywany iterator.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Parametry

*prawy* iterator, który ma pełnić przechowywany iterator.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje przechowywany iterator przy użyciu jego domyślnego konstruktora. Pozostałe konstruktory inicjują przechowywanego iteratora z `base.base()`.

## <a name="op_add_eq"></a>  move_iterator::operator +=

Dodaje przesunięcie do przechowywanego iteratora, tak, aby przechowywany iterator wskazuje na element w nowych bieżącej lokalizacji. Operator spowoduje przesunięcie nowe bieżącego elementu.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

*_Off* przesunięcie do dodania do aktualnej pozycji, aby określić nowy bieżącej pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nowy bieżącego elementu.

### <a name="remarks"></a>Uwagi

Dodaje operator *_Off* przechowywanego iteratora. Następnie zwraca `*this`.

## <a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=

Przechodzi przez określoną liczbę poprzednich elementów. Ten operator odejmowania przesunięcie od przechowywanego iteratora.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator ocenia `*this += -_Off`. Następnie zwraca `*this`.

## <a name="op_add_add"></a>  move_iterator::operator ++

Inkrementuje przechowywany iterator, który należy do tego `move_iterator.` bieżący element jest dostępny przez postinkrementacyjne operatora. Następny element jest dostępny przez preincrement operatora.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy operator (operacja preinkrementacji) inkrementuje przechowywany iterator. Następnie zwraca `*this`.

Drugi operator (postincrement) wykonuje kopię `*this`, ocenia `++*this`. Następnie zwraca kopię.

## <a name="op_add"></a>  move_iterator::operator +

Zwraca pozycję iteratora zaawansowane przez dowolną liczbę elementów.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a>  move_iterator::operator]

Umożliwia dostęp do indeksu tablicy elementów w zakresie `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `(reference)*(*this + _Off)`.

## <a name="move_iterator__operator--"></a>  move_iterator::operator--

Operatory wstępnej i postdekrementacyjne elementów członkowskich przeprowadzania dekrementacji przechowywany iterator.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Pierwszy zmniejsza — operator (operacja predekrementacji) elementu członkowskiego przechowywany iterator. Następnie zwraca `*this`.

Drugi operator (postdecrement) wykonuje kopię `*this`, ocenia `--*this`. Następnie zwraca kopię.

## <a name="move_iterator__operator-"></a>  move_iterator::operator-

Dekrementuje przechowywanego iteratora i zwraca podaną wartość.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Parametry

### <a name="remarks"></a>Uwagi

Operator zwraca `move_iterator(*this) -= _Off`.

## <a name="op_star"></a>  move_iterator::operator *

Dereferencji przechowywanego iteratora i zwraca wartość. To zachowuje się jak `rvalue reference` i wykonuje przeniesienia przypisania. Operator przesyła bieżącego elementu z iteratora podstawowego. Element, który następuje po staje się nowe bieżącego elementu.

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

Typ `pointer` jest **typedef** oparte na iteratora losowego `RandomIterator` dla `move_iterator`i mogą być używane zamiennie.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `RandomIterator`.

## <a name="reference"></a>  move_iterator::Reference

Typ `reference` jest **typedef** na podstawie `value_type&&` dla `move_iterator`i może być używany zamiennie z `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `value_type&&`, który jest odwołaniem rvalue.

## <a name="value_type"></a>  move_iterator::value_type

Typ `value_type` jest `move_iterator` `typedef` oparte na cech iteratora `value_type`i może być używany zamiennie z nim.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla cech iteratora `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Konstruktory przenoszące i przenoszące operatory przypisania (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
