---
title: Klasa initializer_list
ms.date: 11/04/2016
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
ms.openlocfilehash: acd11f3b3a3bf0ba17e34a802cc8988410e17b12
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455363"
---
# <a name="initializerlist-class"></a>Klasa initializer_list

Zapewnia dostęp do tablicy elementów, w których każdy element członkowski jest określonego typu.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ danych elementu, który ma być przechowywany w `initializer_list`.|

## <a name="remarks"></a>Uwagi

`initializer_list` Można utworzyć za pomocą listy inicjalizatora w nawiasach klamrowych:

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Kompilator przekształca listę inicjatorów klamrowych z jednorodnymi elementami na `initializer_list` zawsze, gdy podpis funkcji `initializer_list`wymaga. Aby uzyskać więcej informacji na `initializer_list`temat korzystania z programu, zobacz jednolite [Inicjowanie i delegowanie konstruktorów](../cpp/uniform-initialization-and-delegating-constructors.md)

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[initializer_list](../standard-library/forward-list-class.md#forward_list)|Konstruuje obiekt typu `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|value_type|Typ elementów w `initializer_list`.|
|reference|Typ, który zawiera odwołanie do elementu w `initializer_list`.|
|const_reference|Typ, który dostarcza stałe odwołanie do elementu w `initializer_list`.|
|size_type|Typ, który reprezentuje liczbę elementów w `initializer_list`.|
|iterator|Typ, który dostarcza iterator dla `initializer_list`.|
|const_iterator|Typ, który zapewnia stały iterator dla `initializer_list`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[begin](#begin)|Zwraca wskaźnik do pierwszego elementu w `initializer_list`.|
|[punktów](#end)|Zwraca wskaźnik do jednego z ostatniego elementu w `initializer_list`.|
|[zmienia](#size)|Zwraca liczbę elementów w `initializer_list`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<initializer_list >

**Przestrzeń nazw:** std

## <a name="begin"></a>initializer_list:: BEGIN

Zwraca wskaźnik do pierwszego elementu w `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu `initializer_list`. Jeśli lista jest pusta, wskaźnik jest taki sam dla początku i końca listy.

### <a name="remarks"></a>Uwagi

## <a name="end"></a>initializer_list:: end

Zwraca wskaźnik do jednego z ostatniego elementu w `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do jednego ostatniego elementu na liście. Jeśli lista jest pusta, jest taka sama jak wskaźnik do pierwszego elementu na liście.

## <a name="initializer_list"></a>initializer_list::initializer_list

Konstruuje obiekt typu `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pierwszego*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*Ostatniego*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|

### <a name="remarks"></a>Uwagi

`initializer_list` Jest oparta na tablicy obiektów określonego typu. `initializer_list` Kopiowanie tworzy drugie wystąpienie listy wskazujące te same obiekty; źródłowe obiekty nie są kopiowane.

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

## <a name="size"></a>initializer_list:: size

Zwraca liczbę elementów na liście.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na liście.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[<forward_list>](../standard-library/forward-list.md)
