---
title: klasa tablicy (standardowa biblioteka C++)| Dokumenty firmy Microsoft
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
ms.openlocfilehash: 90c68d00475a622ec89b81cc86639f63b1190d02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364942"
---
# <a name="array-class-c-standard-library"></a>klasa tablicowa (standardowa biblioteka C++)

W tym artykule opisano `N` obiekt, który `Ty`kontroluje sekwencję długości elementów typu . Sekwencja jest przechowywana `Ty`jako tablica `array<Ty, N>` , zawarta w obiekcie.

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
|[Const_reverse_iterator](#const_reverse_iterator)|Typ stałego iteratora wstecznego dla kontrolowanej sekwencji.|
|[difference_type](#difference_type)|Typ odległości ze znakiem między dwoma elementami.|
|[Sterująca](#iterator)|Typ iteratora dla kontrolowanej sekwencji.|
|[pointer](#pointer)|Typ wskaźnika do elementu.|
|[Odwołanie](#reference)|Typ odwołania do elementu.|
|[Reverse_iterator](#reverse_iterator)|Typ odwrotnego iteratora dla kontrolowanej sekwencji.|
|[size_type](#size_type)|Typ odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ elementu.|

|Funkcja elementów członkowskich|Opis|
|-|-|
|[tablica](#array)|Konstruuje obiekt tablicy.|
|[Przypisać](#assign)|(Przestarzałe. Użyj `fill`.) Zastępuje wszystkie elementy.|
|[O](#at)|Uzyskuje dostęp do elementu w określonym położeniu.|
|[Wstecz](#back)|Uzyskuje dostęp do ostatniego elementu.|
|[Rozpocząć](#begin)|Określa początek kontrolowanej sekwencji.|
|[cbegin ( cbegin )](#cbegin)|Zwraca iteratora współrzędnych dostępu losowego do pierwszego elementu w tablicy.|
|[cend](#cend)|Zwraca iterator const dostępu losowego, który wskazuje tuż za końcem tablicy.|
|[Crbegin](#crbegin)|Zwraca iteratora konspiratora do pierwszego elementu w odwróconej tablicy.|
|[Crend](#crend)|Zwraca iteratora konspiratora na końcu odwróconej tablicy.|
|[Danych](#data)|Pobiera adres pierwszego elementu.|
|[Pusty](#empty)|Sprawdza, czy elementy są obecne.|
|[Końcu](#end)|Określa koniec kontrolowanej sekwencji.|
|[fill](#fill)|Zastępuje wszystkie elementy określoną wartością.|
|[Przednie](#front)|Uzyskuje dostęp do pierwszego elementu.|
|[Max_size](#max_size)|Liczy liczbę elementów.|
|[rbegin (rbegin)](#rbegin)|Wyznacza początek odwróconej kontrolowanej sekwencji.|
|[Rend](#rend)|Wyznacza koniec odwróconej kontrolowanej sekwencji.|
|[Rozmiar](#size)|Liczy liczbę elementów.|
|[Wymiany](#swap)|Zamienia zawartości dwóch kontenerów.|

|Operator|Opis|
|-|-|
|[tablica::operator=](#op_eq)|Zastępuje kontrolowaną sekwencję.|
|[tablica::operator\[\]](#op_at)|Uzyskuje dostęp do elementu w określonym położeniu.|

## <a name="remarks"></a>Uwagi

Typ ma domyślny `array()` konstruktor i `operator=`domyślny operator przypisania i spełnia `aggregate`wymagania dla pliku . W związku z `array<Ty, N>` tym obiekty typu można zainicjować przy użyciu inicjatora agregacji. Na przykład:

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

tworzy obiekt, `ai` który zawiera cztery wartości całkowite, inicjuje pierwsze trzy elementy do wartości 1, 2 i 3, odpowiednio, i inicjuje czwarty element do 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> tablicy

**Przestrzeń nazw:** std

## <a name="arrayarray"></a><a name="array"></a>tablica::tablica

Konstruuje obiekt tablicy.

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt lub zakres do wstawienia.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor `array()` pozostawia kontrolowaną sekwencję niezainicjowaną (lub domyślnie zainicjowana). Służy do określania niezainicjowanej sekwencji kontrolowanej.

Konstruktor `array(const array& right)` kopii inicjuje kontrolowaną sekwencję z sekwencją [*prawo*`.begin()`, *prawo*`.end()`). Służy do określenia początkowej kontrolowanej sekwencji, która jest kopią sekwencji kontrolowanej przez obiekt tablicy *po prawej stronie*.

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

## <a name="arrayassign"></a><a name="assign"></a>tablica::przypisywanie

Przestarzałe w C++11, zastąpione [wypełnieniem](#fill). Zastępuje wszystkie elementy.

## <a name="arrayat"></a><a name="at"></a>tablica::w

Uzyskuje dostęp do elementu w określonym położeniu.

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>Parametry

*wył.*\
Położenie elementu dostępu.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich zwracają odwołanie do elementu kontrolowanej sekwencji przy *wyłączonym*położeniu . Jeśli ta pozycja jest nieprawidłowa, funkcja `out_of_range`zgłasza obiekt klasy .

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

## <a name="arrayback"></a><a name="back"></a>tablica::powrót

Uzyskuje dostęp do ostatniego elementu.

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do ostatniego elementu kontrolowanej sekwencji, która musi być niepusta.

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

## <a name="arraybegin"></a><a name="begin"></a>tablica::begin

Określa początek kontrolowanej sekwencji.

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają iteratora dostępu losowego, który wskazuje na pierwszy element sekwencji (lub po prostu poza koniec pustej sekwencji).

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

## <a name="arraycbegin"></a><a name="cbegin"></a>tablica::cbegin

Zwraca **iterator konspiratora,** który odnosi się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu losowego, który wskazuje pierwszy element zakresu lub lokalizację tuż za końcem pustego zakresu (dla pustego **const** `cbegin() == cend()`zakresu).

### <a name="remarks"></a>Uwagi

Z wartością `cbegin`zwracaną , elementy w zakresie nie mogą być modyfikowane.

Tej funkcji elementu członkowskiego można `begin()` użyć zamiast funkcji elementu członkowskiego, aby zagwarantować, że zwracana jest `const_iterator`wartość . Zazwyczaj jest on używany w połączeniu ze słowem kluczowym [auto](../cpp/auto-cpp.md) odliczanie typu, jak pokazano w poniższym przykładzie. W przykładzie `Container` należy wziąć pod uwagę modyfikowalne (non-const) kontener wszelkiego rodzaju, który obsługuje **const** `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="arraycend"></a><a name="cend"></a>tablica::cend

Zwraca **iterator const,** który odnosi się do lokalizacji tuż poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend`służy do testowania, czy iterator przeszedł koniec jego zakresu.

Tej funkcji elementu członkowskiego można `end()` użyć zamiast funkcji elementu członkowskiego, aby zagwarantować, że zwracana jest `const_iterator`wartość . Zazwyczaj jest on używany w połączeniu ze słowem kluczowym [auto](../cpp/auto-cpp.md) odliczanie typu, jak pokazano w poniższym przykładzie. W przykładzie `Container` należy wziąć pod uwagę modyfikowalne (non-const) kontener wszelkiego rodzaju, który obsługuje **const** `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

## <a name="arrayconst_iterator"></a><a name="const_iterator"></a>tablica::const_iterator

Typ iteratora stałego dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stały iterator dostępu losowego dla kontrolowanej sekwencji.

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

## <a name="arrayconst_pointer"></a><a name="const_pointer"></a>tablica::const_pointer

Typ stałego wskaźnika do elementu.

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stały wskaźnik do elementów sekwencji.

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

## <a name="arrayconst_reference"></a><a name="const_reference"></a>tablica::const_reference

Typ stałego odwołania do elementu.

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stałe odwołanie do elementu kontrolowanej sekwencji.

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

## <a name="arrayconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>tablica::const_reverse_iterator

Typ stałego iteratora wstecznego dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako stały iterator odwrotny dla kontrolowanej sekwencji.

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

## <a name="arraycrbegin"></a><a name="crbegin"></a>tablica::crbegin

Zwraca iteratora konspiratora do pierwszego elementu w odwróconej tablicy.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Const reverse random-access iterator adresowania pierwszy element w odwróconej tablicy lub adresowania, co było ostatnim elementem w tablicy nieodwrotowej.

### <a name="remarks"></a>Uwagi

Z wartością `crbegin`zwracaną obiektu tablicy nie można modyfikować.

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

## <a name="arraycrend"></a><a name="crend"></a>tablica::crend

Zwraca iterator konspiratora, który odnosi się do lokalizacji, która zastępuje ostatni element w odwróconej tablicy.

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Const reverse random-access iterator, który adresuje lokalizację po ostatniej pozycji elementu w odwróconej tablicy (lokalizacja, która poprzedziła pierwszy element w tablicy nieodwrotowej).

### <a name="remarks"></a>Uwagi

`crend`jest używany z odwróconą tablicą, tak jak [tablica::cend](#cend) jest używana z tablicą.

Z zwracaną `crend` wartością (odpowiednio zduchrzeni), obiekt tablicy nie może być modyfikowany.

`crend`można sprawdzić, czy odwrotnej iterator osiągnął koniec jego tablicy.

Wartość zwrócona `crend` przez nie powinny być wyłuskiwane.

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

## <a name="arraydata"></a><a name="data"></a>tablica::data

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

## <a name="arraydifference_type"></a><a name="difference_type"></a>tablica::dfference_type

Typ odległości ze znakiem między dwoma elementami.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej podpisu opisuje obiekt, który może reprezentować różnicę między adresami dowolnych dwóch elementów w kontrolowanej sekwencji. Jest synonimem typu `std::ptrdiff_t`.

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

## <a name="arrayempty"></a><a name="empty"></a>tablica::empty

Sprawdza, czy nie ma żadnych elementów.

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `N == 0`wartość true tylko wtedy, gdy .

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

## <a name="arrayend"></a><a name="end"></a>tablica::end

Określa koniec kontrolowanej sekwencji.

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają iteratora dostępu losowego, który wskazuje tuż za końcem sekwencji.

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

## <a name="arrayfill"></a><a name="fill"></a>tablica::wypełnienie

Wymazywanie tablicy i kopiuje określone elementy do pustej tablicy.

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Val*|Wartość elementu wstawianego do tablicy.|

### <a name="remarks"></a>Uwagi

`fill`zastępuje każdy element tablicy określoną wartością.

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
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="arrayfront"></a><a name="front"></a>tablica::przód

Uzyskuje dostęp do pierwszego elementu.

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwołanie do pierwszego elementu kontrolowanej sekwencji, która musi być niepusta.

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

## <a name="arrayiterator"></a><a name="iterator"></a>tablica::iterator

Typ iteratora dla kontrolowanej sekwencji.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako iterator dostępu losowego dla kontrolowanej sekwencji.

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

## <a name="arraymax_size"></a><a name="max_size"></a>tablica::max_size

Liczy liczbę elementów.

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu `N`członkowskiego zwraca .

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

## <a name="arrayoperator"></a><a name="op_at"></a>tablica::operator[]

Uzyskuje dostęp do elementu w określonym położeniu.

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>Parametry

*wył.*\
Położenie elementu dostępu.

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich zwracają odwołanie do elementu kontrolowanej sekwencji przy *wyłączonym*położeniu . Jeśli ta pozycja jest nieprawidłowa, zachowanie jest niezdefiniowane.

Istnieje również non-element [get](array-functions.md#get) funkcja dostępna, aby uzyskać odwołanie do elementu **tablicy**.

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

## <a name="arrayoperator"></a><a name="op_eq"></a>tablica::operator=

Zastępuje kontrolowaną sekwencję.

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Kontener do skopiowania.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego przypisuje każdy element *prawa* do odpowiedniego elementu `*this`kontrolowanej sekwencji, a następnie zwraca . Można go użyć do zastąpienia kontrolowanej sekwencji kopią kontrolowanej sekwencji *w prawej*.

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

## <a name="arraypointer"></a><a name="pointer"></a>tablica::pointer

Typ wskaźnika do elementu.

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako wskaźnik do elementów sekwencji.

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

## <a name="arrayrbegin"></a><a name="rbegin"></a>tablica::rbegin

Wyznacza początek odwróconej kontrolowanej sekwencji.

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwrotnej iteratora, który wskazuje tuż za koniec kontrolowanej sekwencji. W związku z tym wyznacza początek odwrotnej sekwencji.

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

## <a name="arrayreference"></a><a name="reference"></a>tablica::odwołanie

Typ odwołania do elementu.

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako odwołanie do elementu kontrolowanej sekwencji.

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

## <a name="arrayrend"></a><a name="rend"></a>tablica::rend

Wyznacza koniec odwróconej kontrolowanej sekwencji.

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają odwrotnej iteratora, który wskazuje na pierwszy element sekwencji (lub po prostu poza koniec pustej sekwencji)). W związku z tym wyznacza koniec sekwencji odwrotnej.

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

## <a name="arrayreverse_iterator"></a><a name="reverse_iterator"></a>tablica::reverse_iterator

Typ odwrotnego iteratora dla kontrolowanej sekwencji.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może służyć jako odwrotnej iterator dla kontrolowanej sekwencji.

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

## <a name="arraysize"></a><a name="size"></a>tablica::size

Liczy liczbę elementów.

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu `N`członkowskiego zwraca .

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

## <a name="arraysize_type"></a><a name="size_type"></a>tablica::size_type

Typ niepodpisanej odległości między dwoma elementami.

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>Uwagi

Niepodpisany typ liczby całkowitej opisuje obiekt, który może reprezentować długość dowolnej kontrolowanej sekwencji. Jest synonimem typu `std::size_t`.

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

## <a name="arrayswap"></a><a name="swap"></a>tablica::swap

Zamienia zawartość tej tablicy z inną tablicą.

```cpp
void swap(array& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Tablica do wymiany zawartości z.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowane `*this` sekwencje między i *po prawej stronie*. Wykonuje szereg przypisań elementów i wywołań `N`konstruktora proporcjonalnie do .

Istnieje również funkcja [wymiany](array-functions.md#swap) niebędącej członkiem dostępna do wymiany dwóch wystąpień **tablicy.**

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

## <a name="arrayvalue_type"></a><a name="value_type"></a>tablica::value_type

Typ elementu.

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Ty`szablonu .

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

## <a name="see-also"></a>Zobacz też

[\<>tablicowe](../standard-library/array.md)
