---
title: Array — klasa (standardowa biblioteka C++) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: 6f32519e56e42620caec755e6c250d0ee93c6677
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518974"
---
# <a name="array-class-c-standard-library"></a>Array — klasa (standardowa biblioteka C++)

Opisuje obiekt, który kontroluje sekwencje o długości `N` elementów typu `Ty`. Sekwencja jest przechowywany jako tablicę `Ty`, zawarty w `array<Ty, N>` obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`Ty`|Typ elementu.|
|`N`|Liczba elementów.|

## <a name="members"></a>Elementy członkowskie

|Definicja typu|Opis|
|-|-|
|[const_iterator](#const_iterator)|Typ iteratora stałego dla kontrolowanej sekwencji.|
|[const_pointer](#const_pointer)|Typ stałego wskaźnika do elementu.|
|[const_reference](#const_reference)|Typ stałego odwołania do elementu.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.|
|[difference_type](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[iterator](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[pointer](#pointer)|Typ wskaźnika do elementu.|
|[Odwołanie](#reference)|Typ odwołania do elementu.|
|[reverse_iterator](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|-|-|
|[Tablica](#array)|Konstruuje obiekt, tablica.|
|[Przypisz](#assign)|Zamienia wszystkie elementy.|
|[at](#at)|Uzyskuje dostęp do elementu na określonej pozycji.|
|[back](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[begin](#begin)|Określa początek kontrolowanej sekwencji.|
|[cbegin](#cbegin)|Zwraca stały iterator dostępu losowego do pierwszego elementu w tablicy.|
|[cend](#cend)|Zwraca stały iterator dostępu swobodnego, który wskazuje tuż za koniec tablicy.|
|[crbegin](#crbegin)|Zwraca const iterator do pierwszego elementu w odwróconym tablicy.|
|[crend —](#crend)|Zwraca const iterator do końca tablicy odwróconej.|
|[Dane](#data)|Pobiera adres pierwszego elementu.|
|[pusty](#empty)|Testy, czy elementy są obecne.|
|[koniec](#end)|Określa koniec kontrolowanej sekwencji.|
|[Wypełnienie](#fill)|Zamienia wszystkie elementy z określoną wartością.|
|[Frontonu](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[max_size](#max_size)|Liczy liczbę elementów.|
|[rbegin](#rbegin)|Określa początek kontrolowanej sekwencji odwróconej.|
|[rend —](#rend)|Określa koniec kontrolowanej sekwencji odwróconej.|
|[Rozmiar](#size)|Liczy liczbę elementów.|
|[swap](#swap)|Zamienia zawartości dwóch kontenerów.|

|Operator|Opis|
|-|-|
|[Array::operator =](#op_eq)|Zastępuje kontrolowanej sekwencji.|
|[Array::operator]](#op_at)|Uzyskuje dostęp do elementu na określonej pozycji.|

## <a name="remarks"></a>Uwagi

Typ ma domyślny konstruktor `array()` i operator przypisania domyślne `operator=`i spełnia wymagania dotyczące `aggregate`. W związku z tym, obiekty typu `array<Ty, N>` mogą być inicjowane za pomocą inicjatora agregacji. Na przykład

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

Tworzy obiekt `ai` zawierający cztery liczby całkowitej wartości odpowiednio inicjuje pierwsze trzy elementy do wartości 1, 2 i 3 i inicjuje czwarty element na wartość 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<tablicy >

**Namespace:** standardowe

## <a name="array"></a>  Array::Array —

Konstruuje obiekt, tablica.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt lub zakresu do wstawienia.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor `array()` pozostawia kontrolowanej sekwencji niezainicjowana (lub zainicjowane domyślnie). Umożliwia ona określenie niezainicjowanej kontrolowanej sekwencji.

Konstruktor kopiujący `array(const array& right)` inicjuje kontrolowanej sekwencji za pomocą sekwencji [*prawo*`.begin()`, *prawo*`.end()`). Umożliwia ona określenie początkowej kontrolowanej sekwencji, który jest kopią na sekwencję kontrolowaną przez obiekt array *prawo*.

### <a name="example"></a>Przykład

```cpp
// std__array__array_array.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1(c0);

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="assign"></a>  Array::ASSIGN

Przestarzałe w programie C ++ 11, zastępuje [wypełnienia](#fill). Zamienia wszystkie elementy.

```cpp
void assign(const Ty& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość do przypisania.

### <a name="remarks"></a>Uwagi

Funkcji składowej zastępuje sekwencji kontrolowanej przez `*this` z powtórzenia `N` elementów wartości *val*.

### <a name="example"></a>Przykład

```cpp
// std__array__array_assign.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1.assign(4);

// display contents " 4 4 4 4"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 4 4 4
```

## <a name="at"></a>  Array::AT

Uzyskuje dostęp do elementu na określonej pozycji.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

*Wyłączone*<br/>
Pozycja elementu, aby uzyskać dostęp.

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają odwołanie do elementu w kontrolowanej sekwencji w położeniu *poza*. Jeśli tej pozycji jest nieprawidłowa, funkcja zgłasza obiekt klasy `out_of_range`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_at.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
    }
```

## <a name="back"></a>  Array::back

Uzyskuje dostęp do ostatniego elementu.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają odwołania do ostatniego elementu w kontrolowanej sekwencji, która musi być niepusta.

### <a name="example"></a>Przykład

```cpp
// std__array__array_back.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
3
```

## <a name="begin"></a>  Array::BEGIN

Określa początek kontrolowanej sekwencji.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają iterator dostępu swobodnego, który wskazuje na pierwszy element sekwencji (lub tuż za koniec pustej sekwencji).

### <a name="example"></a>Przykład

```cpp
// std__array__array_begin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="cbegin"></a>  Array::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  Array::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator minął koniec swojego zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

## <a name="const_iterator"></a>  Array::const_iterator

Typ iteratora stałego dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stały iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_const_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::const_iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="const_pointer"></a>  Array::const_pointer

Typ stałego wskaźnika do elementu.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stały wskaźnik do elementów w sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_const_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="const_reference"></a>  Array::const_reference

Typ stałego odwołania do elementu.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stałe odwołanie do elementu w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_const_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="const_reverse_iterator"></a>  Array::const_reverse_iterator

Typ iteratora odwrotnego stałego dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stałe odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_const_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
3
```

## <a name="crbegin"></a>  Array::crbegin

Zwraca const iterator do pierwszego elementu w odwróconym tablicy.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, odnoszący się do pierwszego elementu w odwróconym tablicy lub adresowania, który był ostatnim elementem w tablicy nieodwróconej.

### <a name="remarks"></a>Uwagi

Wartością zwracaną `crbegin`, nie można zmodyfikować obiektu tablicy.

### <a name="example"></a>Przykład

```cpp
// array_crbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="crend"></a>  Array::crend

Zwraca iterator stałych adresujący lokalizację następującą po ostatnim elemencie w odwróconej tablicy.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, który dotyczy lokalizacji następującej po ostatnim elemencie w odwróconej tablicy (miejsca przed pierwszego elementu w tablicy nieodwróconej).

### <a name="remarks"></a>Uwagi

`crend` jest używana z tablicą odwróconej podobnie jak [array::cend](#cend) jest używana z tablicą.

Wartością zwracaną `crend` (odpowiednio wraz z przydzielaniem), tablicy nie można zmodyfikować obiektu.

`crend` można sprawdzać, czy wsteczny iterator osiągnął koniec swojej tablicy.

Wartość zwrócona przez obiekt `crend` nie należy usuwać odwołania.

### <a name="example"></a>Przykład

```cpp
// array_crend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>  Array::Data —

Pobiera adres pierwszego elementu.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają adres pierwszego elementu w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_data.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="difference_type"></a>  Array::difference_type

Typ odległości ze znakiem między dwoma elementami.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej ze znakiem opisuje obiekt, który może reprezentować różnica między adresami którychkolwiek dwóch elementów w kontrolowanej sekwencji. Jest synonimem typu `std::ptrdiff_t`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_difference_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
-4
```

## <a name="empty"></a>  Array::Empty

Sprawdza, czy nie ma żadnych elementów.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca wartość true tylko wtedy, gdy `N == 0`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_empty.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

// display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
false
true
```

## <a name="end"></a>  Array::end

Określa koniec kontrolowanej sekwencji.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają iterator dostępu swobodnego, który wskazuje tuż za koniec sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_end.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
3
```

## <a name="fill"></a>  Array::Fill

Wymazuje tablicą i kopiuje określone elementy do pustej tablicy.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu jest wstawiany do tablicy.|

### <a name="remarks"></a>Uwagi

`fill` zastępuje każdy element tablicy na określoną wartość.

### <a name="example"></a>Przykład

```cpp
// array_fill.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator iter;

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v1.fill(3);
   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="front"></a>  Array::front

Uzyskuje dostęp do pierwszego elementu.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają odwołanie do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta.

### <a name="example"></a>Przykład

```cpp
// std__array__array_front.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="iterator"></a>  Array::iterator

Typ iteratora dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_iterator.cpp
// compile with: /EHsc /W4
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = {0, 1, 2, 3};

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for ( MyArray::iterator it1 = c0.begin();
          it1 != c0.end();
          ++it1 ) {
       std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="max_size"></a>  Array::max_size

Liczy liczbę elementów.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `N`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_max_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4
```

## <a name="op_at"></a>  Array::operator]

Uzyskuje dostęp do elementu na określonej pozycji.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

*Wyłączone*<br/>
Pozycja elementu, aby uzyskać dostęp.

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają odwołanie do elementu w kontrolowanej sekwencji w położeniu *poza*. Jeśli tej pozycji jest nieprawidłowa, zachowanie jest niezdefiniowane.

Istnieje również trzecim [uzyskać](array-functions.md#get) funkcji można uzyskać odwołanie do elementu **tablicy**.

### <a name="example"></a>Przykład

```cpp
// std__array__array_operator_sub.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
1 3
```

## <a name="op_eq"></a>  Array::operator =

Zastępuje kontrolowanej sekwencji.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator składowy przypisuje każdego elementu *prawo* na odpowiadający mu element w kontrolowanej sekwencji powraca `*this`. Umożliwia ona Zastąp kopię kontrolowanej sekwencji w kontrolowanej sekwencji *prawo*.

### <a name="example"></a>Przykład

```cpp
// std__array__array_operator_as.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

// display copied contents " 0 1 2 3"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="pointer"></a>  Array::Pointer

Typ wskaźnika do elementu.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako wskaźnik do elementów w sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_pointer.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="rbegin"></a>  Array::rbegin

Określa początek kontrolowanej sekwencji odwróconej.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają iterator odwrotny, który wskazuje tuż za koniec kontrolowanej sekwencji. W związku z tym Określa początek odwrotnej kolejności.

### <a name="example"></a>Przykład

```cpp
// std__array__array_rbegin.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
3
```

## <a name="reference"></a>  Array::Reference

Typ odwołania do elementu.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako odwołanie do elementu w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_reference.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="rend"></a>  Array::rend

Określa koniec kontrolowanej sekwencji odwróconej.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają iterator odwrotny, na którą wskazuje na pierwszy element sekwencji (lub tuż za koniec pustej sekwencji)). Dzięki temu wskazuje koniec odwrotnej kolejności.

### <a name="example"></a>Przykład

```cpp
// std__array__array_rend.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0
```

## <a name="reverse_iterator"></a>  Array::reverse_iterator

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako odwrotnego iteratora dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// std__array__array_reverse_iterator.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
3
```

## <a name="size"></a>  Array::size

Liczy liczbę elementów.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `N`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_size.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4
```

## <a name="size_type"></a>  Array::size_type

Typ odległości bez znaku między dwoma elementu.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Uwagi

Typ całkowitoliczbowy bez znaku, opisująca obiekt, który może reprezentować długość wszelkie kontrolowanej sekwencji. Jest synonimem typu `std::size_t`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_size_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4
```

## <a name="swap"></a>  Array::swap

Zamienia zawartości tej tablicy przy użyciu innej tablicy.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Tablica do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `*this` i *prawo*. Wykonuje szereg przypisania elementu i Konstruktor wywołuje proporcjonalna do `N`.

Istnieje również trzecim [wymiany](array-functions.md#swap) funkcji dostępnych do wymiany dwóch **tablicy** wystąpień.

### <a name="example"></a>Przykład

```cpp
// std__array__array_swap.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};
    c0.swap(c1);

// display swapped contents " 4 5 6 7"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

// display swapped contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="value_type"></a>  Array::value_type

Typ elementu.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Ty`.

### <a name="example"></a>Przykład

```cpp
// std__array__array_value_type.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        {
        Myarray::value_type val = *it;
        std::cout << " " << val;
        }
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>Zobacz także

[\<array>](../standard-library/array.md)<br/>
