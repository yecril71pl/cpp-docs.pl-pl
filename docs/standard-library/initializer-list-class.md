---
title: Klasa initializer_list | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
dev_langs:
- C++
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.workload:
- cplusplus
ms.openlocfilehash: a3941464c80d254b6675e1982dac952c3f29a0f9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="initializerlist-class"></a>lista_inicjatorów — klasa

Zapewnia dostęp do tablicy elementów, w których każdy element członkowski jest określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Type`|Typ danych elementu mają być przechowywane w `initializer_list`.|


## <a name="remarks"></a>Uwagi

`initializer_list` Można skonstruować za pomocą listy inicjalizatora w nawiasach klamrowych:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilator przekształca listy inicjalizatora w nawiasach klamrowych jednorodnych elementów do `initializer_list` po każdej zmianie wymaga sygnatury funkcji `initializer_list`. Aby uzyskać więcej informacji na temat używania `initializer_list`, zobacz [jednolite inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[initializer_list](../standard-library/forward-list-class.md#forward_list)|Tworzy obiekt typu `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|value_type|Typ elementów w `initializer_list`.|
|reference|Typ, który zawiera odwołanie do elementu `initializer_list`.|
|const_reference|Typ, który zapewnia stałą odwołanie do elementu `initializer_list`.|
|size_type|Typ reprezentujący liczbę elementów w `initializer_list`.|
|iterator|Typ, który udostępnia iteratora dla `initializer_list`.|
|const_iterator|Typ, który zapewnia stałą iteratora dla `initializer_list`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[begin](#begin)|Zwraca wskaźnik do pierwszego elementu w `initializer_list`.|
|[Koniec](#end)|Zwraca wskaźnik do jednego po ostatnim elementem w `initializer_list`.|
|[Rozmiar](#size)|Zwraca liczbę elementów w `initializer_list`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<initializer_list >

**Namespace:** Standard

## <a name="begin"></a>  initializer_list::BEGIN

Zwraca wskaźnik do pierwszego elementu w `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu obiektu `initializer_list`. Jeśli lista jest pusta, wskaźnika jest taki sam dla początek i koniec listy.

### <a name="remarks"></a>Uwagi

## <a name="end"></a>  initializer_list::end

Zwraca wskaźnik do jednego po ostatnim elementem w `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego po ostatnim elementem na liście. Jeśli lista jest pusta, jest taka sama jak wskaźnik do pierwszego elementu na liście.

## <a name="initializer_list"></a>  initializer_list::initializer_list

Tworzy obiekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|

### <a name="remarks"></a>Uwagi

`initializer_list` Opiera się na tablicę obiektów określonego typu. Kopiowanie `initializer_list` tworzy drugie wystąpienie listy wskazuje na te same obiekty; obiektów nie są kopiowane.

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

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3c2 = 5 4 3 2 1c3 = 5 4 3 2 1c4 = 5 4c5 = 5 4
```

## <a name="size"></a>  initializer_list::size

Zwraca liczbę elementów na liście.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[<forward_list>](../standard-library/forward-list.md)<br/>
