---
title: Array — Klasa (standardowa biblioteka C++) | Microsoft Docs
ms.date: 11/13/2019
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
ms.openlocfilehash: a6cda0f0c66624158f7c2abfeabb5f54678d21b0
ms.sourcegitcommit: 7b12cc4a4d3fcb261d67420fc3dd18652730008f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82643648"
---
# <a name="array-class-c-standard-library"></a>Array — Klasa (standardowa biblioteka C++)

Opisuje obiekt, który kontroluje sekwencję długości `N` elementów typu. `Ty` Sekwencja jest przechowywana w postaci tablicy `Ty`, zawartej w `array<Ty, N>` obiekcie.

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
|[const_reverse_iterator](#const_reverse_iterator)|Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.|
|[difference_type](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[Iterator](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[pointer](#pointer)|Typ wskaźnika do elementu.|
|[odwoła](#reference)|Typ odwołania do elementu.|
|[reverse_iterator](#reverse_iterator)|Typ iteratora odwrotnego dla kontrolowanej sekwencji.|
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|-|-|
|[tablica](#array)|Konstruuje obiekt Array.|
|[ponownie](#assign)|Zbędn. Użyj `fill`.) Zamienia wszystkie elementy.|
|[w](#at)|Uzyskuje dostęp do elementu w określonej pozycji.|
|[Wstecz](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[zaczną](#begin)|Określa początek kontrolowanej sekwencji.|
|[cbegin](#cbegin)|Zwraca iterator const dostępu swobodnego do pierwszego elementu w tablicy.|
|[cend](#cend)|Zwraca iterator const dostępu swobodnego, który wskazuje tuż poza końcem tablicy.|
|[crbegin —](#crbegin)|Zwraca iterator const do pierwszego elementu w odwróconej tablicy.|
|[crend](#crend)|Zwraca iterator const do końca odwróconej tablicy.|
|[Data](#data)|Pobiera adres pierwszego elementu.|
|[puste](#empty)|Testuje, czy elementy są obecne.|
|[punktów](#end)|Określa koniec kontrolowanej sekwencji.|
|[fill](#fill)|Zastępuje wszystkie elementy określoną wartością.|
|[FSB](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[max_size](#max_size)|Liczy liczbę elementów.|
|[rbegin](#rbegin)|Określa początek odwróconej sekwencji kontrolowanej.|
|[rend](#rend)|Określa koniec odwróconej kontrolowanej sekwencji.|
|[size](#size)|Liczy liczbę elementów.|
|[wymiany](#swap)|Zamienia zawartości dwóch kontenerów.|

|Operator|Opis|
|-|-|
|[Array:: operator =](#op_eq)|Zastępuje kontrolowaną sekwencję.|
|[Array:: operator\[\]](#op_at)|Uzyskuje dostęp do elementu w określonej pozycji.|

## <a name="remarks"></a>Uwagi

Typ ma konstruktora `array()` domyślnego i domyślnego operatora `operator=`przypisania i spełnia wymagania dla. `aggregate` W związku z tym obiekty `array<Ty, N>` typu mogą być inicjowane za pomocą inicjatora agregacji. Na przykład:

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

Tworzy obiekt `ai` , który przechowuje cztery wartości całkowite, inicjuje pierwsze trzy elementy odpowiednio do wartości 1, 2 i 3, i inicjuje czwarty element do 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> tablicy

**Przestrzeń nazw:** std

## <a name="arrayarray"></a><a name="array"></a>Array:: Array

Konstruuje obiekt Array.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt lub zakres do wstawienia.

### <a name="remarks"></a>Uwagi

Konstruktor `array()` domyślny pozostawia kontrolowanej sekwencji niezainicjowanej (lub domyślnie zainicjowany). Służy do określania niezainicjowanej kontrolowanej sekwencji.

Konstruktor `array(const array& right)` kopiujący inicjuje kontrolowaną sekwencję z sekwencją [*Right*`.begin()`, *Right*`.end()`). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej *przez obiekt Array*.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arrayassign"></a><a name="assign"></a>Array:: Assign

Przestarzałe w języku C++ 11, zastąpione przez [wypełnienie](#fill). Zamienia wszystkie elementy.

## <a name="arrayat"></a><a name="at"></a>Array:: at

Uzyskuje dostęp do elementu w określonej pozycji.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

*Logowanie*\
Pozycja elementu do uzyskania dostępu.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do elementu kontrolowanej sekwencji w pozycji *wyłączone*. Jeśli ta pozycja jest nieprawidłowa, funkcja zgłasza obiekt klasy `out_of_range`.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="arrayback"></a><a name="back"></a>Array:: Back

Uzyskuje dostęp do ostatniego elementu.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do ostatniego elementu kontrolowanej sekwencji, która nie może być pusta.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraybegin"></a><a name="begin"></a>Array:: BEGIN

Określa początek kontrolowanej sekwencji.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają Iterator dostępu swobodnego, który wskazuje na pierwszy element sekwencji (lub tuż poza końcem pustej sekwencji).

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraycbegin"></a><a name="cbegin"></a>Array:: cbegin

Zwraca iterator **const** , który dotyczy pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator **stałej** dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji `begin()` składowej, aby zagwarantować, że wartość zwracana to `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener **const**dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>Array:: cend

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji `end()` składowej, aby zagwarantować, że wartość zwracana to `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy `Container` , że jest to modyfikowalny kontener **const**dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie można usunąć odwołania `cend` do wartości zwracanej przez.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>Array:: const_iterator

Typ iteratora stałego dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może być używany jako iterator stałego dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
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

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>Array:: const_pointer

Typ stałego wskaźnika do elementu.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako stały wskaźnik do elementów sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayconst_reference"></a><a name="const_reference"></a>Array:: const_reference

Typ stałego odwołania do elementu.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może stanowić stałe odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>Array:: const_reverse_iterator

Typ iteratora stałego zwrotnego dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może być używany jako ciągły iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraycrbegin"></a><a name="crbegin"></a>Array:: crbegin —

Zwraca iterator const do pierwszego elementu w odwróconej tablicy.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu stała odwrotnie dostęp losowy odnoszący się do pierwszego elementu w odwróconej tablicy lub na adres, który był ostatnim elementem w nieodwróconej tablicy.

### <a name="remarks"></a>Uwagi

Z wartością `crbegin`zwracaną nie można zmodyfikować obiektu Array.

### <a name="example"></a>Przykład

```cpp
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

## <a name="arraycrend"></a><a name="crend"></a>Array:: crend

Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej tablicy.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu const odwrotnie dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w odwróconej tablicy (lokalizacja, która poprzedza pierwszy element w nieodwróconej tablicy).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconą tablicą, tak jak [Array:: cend](#cend) jest używany z tablicą.

Po wartości zwracanej `crend` (odpowiednio zmniejszonej) obiekt Array nie może być modyfikowany.

`crend`może służyć do sprawdzenia, czy iterator odwrotny osiągnął koniec tablicy.

Nie można usunąć odwołania `crend` do wartości zwracanej przez.

### <a name="example"></a>Przykład

```cpp
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

## <a name="arraydata"></a><a name="data"></a>Tablica::d ATA

Pobiera adres pierwszego elementu.

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają adres pierwszego elementu w kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraydifference_type"></a><a name="difference_type"></a>Tablica::d ifference_type

Typ odległości ze znakiem między dwoma elementami.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ Liczba całkowita ze znakiem opisuje obiekt, który może reprezentować różnicę między adresami wszystkich dwóch elementów w kontrolowanej sekwencji. Jest to synonim dla typu `std::ptrdiff_t`.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayempty"></a><a name="empty"></a>Array:: Empty

Sprawdza, czy nie ma żadnych elementów.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość true tylko `N == 0`wtedy, gdy.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayend"></a><a name="end"></a>Array:: end

Określa koniec kontrolowanej sekwencji.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają Iterator dostępu swobodnego, który wskazuje tuż poza końcem sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayfill"></a><a name="fill"></a>Array:: Fill

Wymazuje tablicę i kopiuje określone elementy do pustej tablicy.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*użyte*|Wartość wstawianego elementu do tablicy.|

### <a name="remarks"></a>Uwagi

`fill`zamienia każdy element tablicy na określoną wartość.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>Array:: front

Uzyskuje dostęp do pierwszego elementu.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do pierwszego elementu kontrolowanej sekwencji, która nie może być pusta.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayiterator"></a><a name="iterator"></a>Array:: iterator

Typ iteratora dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może działać jako Iterator dostępu swobodnego dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
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

## <a name="arraymax_size"></a><a name="max_size"></a>Array:: max_size

Liczy liczbę elementów.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `N`wartość.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayoperator"></a><a name="op_at"></a>Array:: operator []

Uzyskuje dostęp do elementu w określonej pozycji.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

*Logowanie*\
Pozycja elementu do uzyskania dostępu.

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do elementu kontrolowanej sekwencji w pozycji *wyłączone*. Jeśli ta pozycja jest nieprawidłowa, zachowanie jest niezdefiniowane.

Dostępna jest również funkcja [Get](array-functions.md#get) poza składową, która umożliwia uzyskanie odwołania do elementu **tablicy**.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayoperator"></a><a name="op_eq"></a>Array:: operator =

Zastępuje kontrolowaną sekwencję.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator członkowski przypisuje każdy element *bezpośrednio* do odpowiadającego elementu kontrolowanej sekwencji, a następnie zwraca `*this`. Służy do zastępowania kontrolowanej sekwencji kopią kontrolowanej sekwencji *po prawej stronie*.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="arraypointer"></a><a name="pointer"></a>Tablica::p ointer

Typ wskaźnika do elementu.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako wskaźnik do elementów sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayrbegin"></a><a name="rbegin"></a>Array:: rbegin

Określa początek odwróconej sekwencji kontrolowanej.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają iterator odwrotny, który wskazuje tuż poza końcem kontrolowanej sekwencji. W związku z tym określa początek sekwencji odwrotnej.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayreference"></a><a name="reference"></a>Array:: Reference

Typ odwołania do elementu.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć jako odwołanie do elementu kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayrend"></a><a name="rend"></a>Array:: rend

Określa koniec odwróconej kontrolowanej sekwencji.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają iterator odwrotny, który wskazuje na pierwszy element sekwencji (lub tuż poza końcem pustej sekwencji)). W związku z tym wyznacza koniec sekwencji odwrotnej.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>Array:: reverse_iterator

Typ iteratora odwrotnego dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może obsłużyć iterator odwrotny dla kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraysize"></a><a name="size"></a>Array:: size

Liczy liczbę elementów.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `N`wartość.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arraysize_type"></a><a name="size_type"></a>Array:: size_type

Typ niepodpisanej odległości między dwoma elementami.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej bez znaku opisuje obiekt, który może reprezentować długość dowolnej kontrolowanej sekwencji. Jest to synonim dla typu `std::size_t`.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
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

## <a name="arrayswap"></a><a name="swap"></a>Array:: swap

Zamienia zawartość tej tablicy na inną tablicę.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Tablica, do której ma zostać zamieniony zawartość.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między `*this` i *po prawej*. Wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do `N`.

Dostępna jest również funkcja [zamiany](array-functions.md#swap) poza składową, która umożliwia zamianę dwóch wystąpień **tablicy** .

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="arrayvalue_type"></a><a name="value_type"></a>Array:: value_type

Typ elementu.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `Ty`szablonu.

### <a name="example"></a>Przykład

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
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

[\<>tablicy](../standard-library/array.md)
