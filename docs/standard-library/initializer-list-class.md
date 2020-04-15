---
title: initializer_list, klasa
description: Odwołanie do klasy initializer_list w bibliotece standardu C++, zaimplementowane przez firmę Microsoft w programie Visual Studio.
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: b1d33ce484948e731f8d3062b7a99df06ef26073
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373360"
---
# <a name="initializer_list-class"></a>initializer_list, klasa

Zapewnia dostęp do tablicy elementów, w których każdy element członkowski jest określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

*Typu*\
Typ danych elementu, który `initializer_list`ma być przechowywany w pliku .

## <a name="remarks"></a>Uwagi

Można `initializer_list` skonstruować przy użyciu listy inicjatora usztywnionego:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilator przekształca usztywnione listy inicjatorów z `initializer_list` jednorodnymi elementami `initializer_list`w każdym przypadku, gdy podpis funkcji wymaga . Aby uzyskać więcej `initializer_list`informacji na temat używania , zobacz [Jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Initializer_list](#initializer_list)|Konstruuje obiekt `initializer_list`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|`value_type`|Typ elementów w `initializer_list`pliku .|
|`reference`|Typ, który zawiera odwołanie do `initializer_list`elementu w .|
|`const_reference`|Typ, który zapewnia stałe odwołanie do `initializer_list`elementu w .|
|`size_type`|Typ reprezentujący liczbę elementów `initializer_list`w pliku .|
|`iterator`|Typ, który zapewnia iterator `initializer_list`dla .|
|`const_iterator`|Typ, który zapewnia stały iterator dla `initializer_list`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Rozpocząć](#begin)|Zwraca wskaźnik do pierwszego elementu `initializer_list`w pliku .|
|[Końcu](#end)|Zwraca wskaźnik do jednego obok ostatniego elementu w pliku `initializer_list`.|
|[Rozmiar](#size)|Zwraca liczbę elementów `initializer_list`w pliku .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<initializer_list>

**Przestrzeń nazw:** std

## <a name="initializer_listbegin"></a><a name="begin"></a>initializer_list::begin

Zwraca wskaźnik do pierwszego elementu `initializer_list`w pliku .

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu `initializer_list`. Jeśli lista jest pusta, wskaźnik jest taki sam dla początku i końca listy.

## <a name="initializer_listend"></a><a name="end"></a>initializer_list::end

Zwraca wskaźnik do jednego obok ostatniego elementu w pliku `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego obok ostatniego elementu na liście. Jeśli lista jest pusta, jest taka sama jak wskaźnik do pierwszego elementu na liście.

## <a name="initializer_listinitializer_list"></a><a name="initializer_list"></a>initializer_list::initializer_list

Konstruuje obiekt `initializer_list`typu .

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Położenie pierwszego elementu w zakresie elementów do skopiowania.

*Ostatnio*\
Położenie pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

### <a name="remarks"></a>Uwagi

An `initializer_list` jest oparty na tablicy obiektów określonego typu. Kopiowanie `initializer_list` tworzy drugie wystąpienie listy wskazującej te same obiekty; obiekty znajdujące się pod spodem nie są kopiowane.

### <a name="example"></a>Przykład

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="initializer_listsize"></a><a name="size"></a>initializer_list::size

Zwraca liczbę elementów na liście.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście.

## <a name="see-also"></a>Zobacz też

[<forward_list>](../standard-library/forward-list.md)
