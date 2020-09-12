---
title: span — Klasa (standardowa biblioteka C++) | Microsoft Docs
description: Dokumentacja interfejsu API dla klasy span (standard Template Library), która zapewnia uproszczony wgląd w ciągłą sekwencję obiektów.
ms.date: 05/28/2020
f1_keywords:
- span/std::span
- span/std::span::const_pointer
- span/std::span::const_reference
- span/std::span::difference_type
- span/std::span::element_type
- span/std::span::iterator
- span/std::span::pointer
- span/std::span::reference
- span/std::span::reverse_iterator
- span/std::span::size_type
- span/std::span::value_type
- span/std::span::at
- span/std::span::assign
- span/std::span::back
- span/std::span::begin
- span/std::span::data
- span/std::span::empty
- span/std::span::end
- span/std::span::front
- span/std::span::rbegin
- span/std::span::rend
- span/std::span::size
- span/std::span::size_bytes
- span/std::span::operator=
- span/std::span::operator[]
helpviewer_keywords:
- std::span [C++]
- std::span [C++], const_pointer
- std::span [C++], const_reference
- std::span [C++], difference_type
- std::span [C++], element_type
- std::span [C++], iterator
- std::span [C++], pointer
- std::span [C++], reference
- std::span [C++], reverse_iterator
- std::span [C++], size_type
- std::span [C++], value_type
- std::span [C++], assign
- std::span [C++], at
- std::span [C++], back
- std::span [C++], begin
- std::span [C++], data
- std::span [C++], empty
- std::span [C++], end
- std::span [C++], front
- std::span [C++], rbegin
- std::span [C++], rend
- std::span [C++], size
- std::span [C++], size_bytes
ms.openlocfilehash: 297104820f5498e59397db9025aed1675984a060
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039967"
---
# <a name="span-class-c-standard-library"></a>span — Klasa (standardowa biblioteka C++)

Zapewnia uproszczony wgląd w ciągłą sekwencję obiektów. Zakres umożliwia bezpieczną metodę iteracji i indeksowania obiektów, które są rozłożone z powrotem do tyłu w pamięci, takich jak obiekty przechowywane w tablicy wbudowanej, `std::array` lub `std::vector` .

Jeśli zwykle uzyskujesz dostęp do sekwencji obiektów zaplecza przy użyciu wskaźnika i indeksu, a `span` jest to bezpieczniejsza, lekki alternatywa.

Rozmiar `span` można ustawić w czasie kompilacji przez określenie go jako argumentu szablonu lub w czasie wykonywania przez określenie `dynamic_extent` .

## <a name="syntax"></a>Składnia

```cpp
template<class T, size_t Extent = dynamic_extent>
class span;
```

### <a name="template-parameters"></a>Parametry szablonu

`T`\
 Typ elementów w zakresie.

`Extent`\
 Liczba elementów w zakresie, jeśli określono w czasie kompilacji. W przeciwnym razie  `std::dynamic_extent` , jeśli liczba elementów zostanie określona w czasie wykonywania.

[Przewodnik odejmowania](#deduction_guides)

## <a name="members"></a>Elementy członkowskie

| **Definicje typu** | **Opis** |
|-|-|
| [const_pointer](#pointer) | Typ wskaźnika do **`const`** elementu. |
| [const_reference](#reference) | Typ odwołania do **`const`** elementu. |
| [difference_type](#difference_type) | Typ odległości ze znakiem między dwoma elementami. |
| [element_type](#element_type) | Typ elementu span. |
| [Iterator](#iterator) | Typ iteratora dla zakresu. |
| [pointer](#pointer) | Typ wskaźnika do elementu. |
| [odwoła](#reference) | Typ odwołania do elementu. |
| [reverse_iterator](#reverse_iterator) | Typ iteratora odwrotnego dla zakresu. |
| [size_type](#size_type) | Typ wyniku niepodpisanej odległości między dwoma elementami w zakresie. |
| [value_type](#value_type) | Typ elementu, bez **`const`** **`volatile`** kwalifikacji lub. |
| **Konstruktory** | **Opis** |
|[span](#span)| Konstrukcja a `span` .|
| **Obsługa iteratora** | **Opis** |
|[zaczną](#begin) | Pobierz iterator wskazujący na pierwszy element w zakresie.|
|[punktów](#end) | Pobierz iterator wskazujący koniec zakresu. |
|[rbegin](#rbegin) | Pobierz iterator odwrotny wskazujący ostatni element zakresu; oznacza to, że początek odwróconego przedziału.|
|[rend](#rend) | Uzyskaj iterator odwrotny wskazujący przód zakresu; oznacza to, że koniec odwróconego zakresu.|
| **Elementy dostępu**| **Opis** |
|[Wstecz](#back) | Pobierz ostatni element z zakresu.|
|[data](#data) | Pobierz adres pierwszego elementu w zakresie.|
|[FSB](#front) | Pobierz pierwszy element z zakresu.|
|[zakład\[\]](#op_at) | Uzyskaj dostęp do elementu w określonej pozycji.|
| **Obserwatorzy** | **Opis** |
|[puste](#empty)| Sprawdź, czy zakres jest pusty.|
|[zmienia](#size) | Pobierz liczbę elementów w zakresie.|
|[size_bytes](#size_bytes) | Pobierz rozmiar zakresu w bajtach.|
| **Przeglądy** | **Opis**|
| [pierwszego](#first_view) | Pobierz Podzakres od początku zakresu.|
| [ostatniego](#last_view) | Pobierz Podzakres z tyłu zakresu.|
| [Podzakres](#sub_view) | Pobierz przedział z dowolnego miejsca w obrębie zakresu.|
| **Operatory** | **Opis** |
|[span:: operator =](#op_eq)| Zastąp zakres.|
|[span:: operator\[\]](#op_at)| Pobierz element na określonej pozycji. |

## <a name="remarks"></a>Uwagi

Wszystkie `span` funkcje składowe mają stałą czasową złożoność.

W przeciwieństwie do `array` lub `vector` , zakres nie jest "własny" elementów wewnątrz niego. Zakres nie zwalnia żadnego magazynu dla elementów znajdujących się w nim, ponieważ nie jest on magazynem dla tych obiektów.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<span>

**Przestrzeń nazw:** std

**Opcja kompilatora:** [/std: c + + Najnowsza](../build/reference/std-specify-language-standard-version.md)

## <a name="spanback"></a><a name="back"></a> `span::back`

Pobierz ostatni element z zakresu.

```cpp
constexpr reference back() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do ostatniego elementu w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << mySpan.back();
}
```

```Output
2
```

## <a name="spanbegin"></a><a name="begin"></a> `span::begin`

Pobierz iterator wskazujący na pierwszy element w zakresie.

```cpp
constexpr iterator begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący na pierwszy element w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.begin();
    cout << *i;
}
```

```Output
0
```

## <a name="spandata"></a><a name="data"></a> `span::data`

Uzyskaj wskaźnik na początku danych zakresu.

```cpp
constexpr pointer data() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego elementu przechowywanego w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    auto i = mySpan.data();
    cout << *i;
}
```

```Output
0
```

## <a name="spandifference_type"></a><a name="difference_type"></a> `span::difference_type`

Liczba elementów między dwoma elementami w zakresie.

```cpp
using difference_type = std::ptrdiff_t;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::difference_type distance = mySpan.end() - mySpan.begin();
    cout << distance << std::endl;
}
```

```Output
3
```

## <a name="spanelement_type"></a><a name="element_type"></a> `span::element_type`

Typ elementów w zakresie.

```cpp
using element_type = T;
```

### <a name="remarks"></a>Uwagi

Typ jest pobierany z parametru szablonu `T` podczas tworzenia zakresu.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::element_type et = mySpan[2];
    cout << et << endl;
}
```

```Output
2
```

## <a name="spanempty"></a><a name="empty"></a> `span::empty`

Czy zakres zawiera elementy.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca **`true`** if `this->size() == 0` . W przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    bool isEmpty = mySpan.empty(); // isEmpty == false
}
```

## <a name="spanend"></a><a name="end"></a> `span::end`

Uzyskaj iterator na końcu zakresu.

```cpp
constexpr iterator end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`end` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Nie odwołuje się do wartości zwracanej przez ten iterator. Użyj go, aby określić, czy iterator osiągnął się poza ostatnim elementem w zakresie.

### <a name="example"></a>Przykład

```cpp
// Iteration
for (auto it = s1.begin(); it != s1.end(); ++it)
{
    cout << *it;
}
```

## <a name="spanfirst"></a><a name="first_view"></a> `span::first`

Uzyskaj Podzakres, pobrany od przodu tego zakresu.

```cpp
constexpr auto first(size_type count) const noexcept;
template <size_t count> constexpr auto first() const noexcept;
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów z przodu tego zakresu, które mają zostać umieszczone w podzakresach.  
Liczba elementów jest określona jako parametr do szablonu lub do funkcji, jak pokazano poniżej.

### <a name="return-value"></a>Wartość zwracana

Zakres, który zawiera `count` elementy z przodu tego zakresu.

### <a name="remarks"></a>Uwagi

Użyj wersji szablonu tej funkcji, jeśli jest to możliwe, aby sprawdzić poprawność `count` w czasie kompilacji i zachować informacje na temat zakresu, ponieważ zwraca on zakres stałego zakresu.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.first(2);
    cout << "mySpan.first(2): ";
    for (auto& i : first2)
    {
        cout << i;
    }

    cout << "\nmySpan.first<2>: ";
    auto viewSpan = mySpan.first<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.first(2): 01
mySpan.first<2>: 01
```

## <a name="spanfront"></a><a name="front"></a> `span::front`

Pobierz pierwszy element z zakresu.

```cpp
constexpr reference front() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto i = mySpan.front();
    cout << i;
}
```

```Output
0
```

## <a name="spaniterator"></a><a name="iterator"></a> `span::iterator`

Typ iteratora nad elementami zakresu.

```cpp
using iterator = implementation-defined-iterator-type;
```

### <a name="remarks"></a>Uwagi

Ten typ służy jako iterator dla elementów w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::iterator it = mySpan.begin();
    cout << *it++ << *it++ << *it;
}
```

```Output
012
```

## <a name="spanlast"></a><a name="last_view"></a> `span::last`

Pobierz Podzakres, pobrany od końca tego zakresu.

```cpp
constexpr span<element_type, dynamic_extent> last(const size_type count) const noexcept;
template <size_t count> constexpr span<element_type, count> last() const noexcept;
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów z końca tego zakresu, które mają zostać umieszczone w przedziale.
Liczba może być określona jako parametr do szablonu lub do funkcji, jak pokazano poniżej.

### <a name="return-value"></a>Wartość zwracana

Zakres zawierający ostatnie `count` elementy z tego zakresu.

### <a name="remarks"></a>Uwagi

Użyj wersji szablonu tej funkcji, jeśli jest to możliwe, aby sprawdzić poprawność `count` w czasie kompilacji i zachować informacje na temat zakresu, ponieważ zwraca on zakres stałego zakresu.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    auto first2 = mySpan.last(2);
    cout << "mySpan.last(2): ";
    for (auto& i : last2)
    {
        cout << i;
    }

    cout << "\nmySpan.last<2>: ";
    auto viewSpan = mySpan.last<2>();
    for (auto& i : viewSpan)
    {
        cout << i;
    }
}
```

```Output
mySpan.last(2): 12
mySpan.last<2>: 12
```

## <a name="spanoperator"></a><a name="op_at"></a> `span::operator[]`

Pobierz element z zakresu w określonym położeniu.

```cpp
constexpr reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Element (liczony od zera) w zakresie do uzyskania dostępu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do elementu w *przesunięciu*położenia. Jeśli pozycja jest nieprawidłowa, zachowanie jest niezdefiniowane.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan[1];
}
```

```Output
1
```

## <a name="spanoperator"></a><a name="op_eq"></a> `span::operator=`

Przypisz kolejny zakres do tego elementu.

```cpp
constexpr span& operator=(const span& other) noexcept = default;
```

### <a name="parameters"></a>Parametry

*różnych*\
Zakres, który ma zostać przypisany do tego elementu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Przypisanie wykonuje skróconą kopię wskaźnika danych i rozmiar. Kopia skrócona jest bezpieczna, ponieważ `span` nie przydziela pamięci dla elementów, które zawiera.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    span<int> mySpan2;
    mySpan2 = mySpan;
    for (auto &i : mySpan2)
    {
        cout << it;
    }
}
```

```Output
012
```

## <a name="spanpointer"></a><a name="pointer"></a> `span::pointer`

Typy wskaźnika i **`const`** wskaźnika do elementu span.

```cpp
using pointer = T*;
using const_pointer = const T*;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // pointer
    span<int>::pointer ptr = &mySpan[2];
    *ptr = 9;
    cout << mySpan[2];

    // const pointer
    span<int>::const_pointer cPtr = &mySpan[0];
    // *cPtr = 9; error - const
    cout << *cPtr;
}
```

```Output
90
```

## <a name="spanrbegin"></a><a name="rbegin"></a> `span::rbegin`

Pobierz iterator odwrotny wskazujący ostatni element tego zakresu.

```cpp
constexpr reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator wskazujący początek odwróconego przedziału.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

```Output
210
```

## <a name="spanreference"></a><a name="reference"></a> `span::reference`

Typy odwołań i **`const`** odwołania do elementu span.

```cpp
using reference = T&;
using const_reference = const T&;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    // reference
    span<int>::reference ref = mySpan[0];
    ref = 9;
    cout << mySpan[0];
    // const reference
    span<int>::const_reference cRef = mySpan[1];
    // cRef = 9; error because const
    cout << cRef;
}
```

```Output
91
```

## <a name="spanrend"></a><a name="rend"></a> `span::rend`

Uzyskaj Iterator dostępu swobodnego, który wskazuje tuż poza końcem odwróconego przedziału.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator odwrotny do symbolu zastępczego po ostatnim elemencie w odwróconym przedziale. oznacza to symbol zastępczy przed pierwszym elementem w odwrót.

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym zakresem, tak jak [zakres:: end](#end) jest używany z zakresem. Służy do sprawdzania, czy iterator odwrotny osiągnął koniec zakresu.

Nie można usunąć odwołania do wartości zwracanej przez nie `rend` .

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    for (auto rIt = s1.rbegin(); rIt != s1.rend(); ++rIt)
    {
        cout << *rIt;
    }
}
```

## <a name="spanreverse_iterator"></a><a name="reverse_iterator"></a> `span::reverse_iterator`

Typ iteratora odwrotnego dla zakresu.

```cpp
using reverse_iterator = std::reverse_iterator<iterator>;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::reverse_iterator rIt = mySpan.rbegin();
    cout << *rIt++ << *rIt++ << *rIt;
}
```

```Output
210
```

## <a name="spansize"></a><a name="size"></a> `span::size`

Pobierz liczbę elementów w zakresie.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size();
}
```

```Output
3
```

## <a name="spansize_bytes"></a><a name="size_bytes"></a> `span::size_bytes`

Pobierz rozmiar elementów w zakresie w bajtach.

```cpp
constexpr size_type size_bytes() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów zajmowanych przez wszystkie elementy w zakresie; oznacza to, że `sizeof(element_type)` pomnożona przez liczbę elementów w zakresie.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);
    cout << mySpan.size_bytes(); // 3 elements * 4 (size of an int)
}
```

```Output
12
```

## <a name="spansize_type"></a><a name="size_type"></a> `span::size_type`

Typ bez znaku, odpowiedni do przechowywania liczby elementów w zakresie.

```cpp
using size_type = size_t;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::size_type szType = mySpan.size();
    cout << szType;
}
```

```Output
3
```

## <a name="spanspan"></a><a name="span"></a> `span::span`

`span` Konstruktor.

```cpp
constexpr span() noexcept
requires (Extent == 0 || Extent == dynamic_extent) = default;

template <class It>
constexpr explicit(Extent != dynamic_extent)
span(It first, size_type count) noexcept

template <class It, class End>
constexpr explicit(Extent != dynamic_extent)
span(It first, End last) noexcept(noexcept(last - first))

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<T (*)[], T (*)[]>
constexpr span(array<T, N>& arr) noexcept

template <class T, size_t N>
requires (Extent == dynamic_extent || Extent == N) && is_convertible_v<const T (*)[], T (*)[]>
constexpr span(const array<T, N>& arr) noexcept

template <size_t N>
requires (Extent == dynamic_extent || Extent == N)
constexpr span(type_identity_t<T> (&arr)[N]) noexcept

template <class R>
constexpr explicit(Extent != dynamic_extent)
span(R&& r)

// default copy ctor
constexpr span(const span& other) noexcept = default;

// converting  ctor
template <class T, size_t OtherExtent>
requires (Extent == dynamic_extent || OtherExtent == dynamic_extent ||
              Extent == OtherExtent) && is_convertible_v<T (*)[], T (*)[]>
constexpr explicit(Extent != dynamic_extent && OtherExtent == dynamic_extent)
span(const span<T, OtherExtent>& other) noexcept
```

### <a name="parameters"></a>Parametry

*Genotyp*\
Utwórz zakres z tablicy.

*liczbą*\
Liczba elementów, które będą należeć do zakresu.

*pierwszego*\
Iterator do pierwszego elementu w zakresie.

*ostatniego*\
Iterator tylko do ostatniego elementu w zakresie.

*Azotan*\
Liczba elementów, które będą należeć do zakresu.

*różnych*\
Utwórz kopię tego zakresu.

*®*\
Utwórz zakres z tego zakresu.

### <a name="remarks"></a>Uwagi

Zakres nie ma wolnego miejsca w magazynie dla elementów w zakresie, ponieważ nie jest on magazynem obiektów w ramach tego zakresu.

|Konstruktor  | Opis  |
|---------|---------|
|`span()` | Konstruowanie pustego zakresu. Brane pod uwagę tylko podczas rozpoznawania przeciążenia, gdy parametrem szablonu `Extent` jest `0` lub `dynamic_extent` .|
|`span(It first, size_type count)` | Zbuduj zakres od pierwszego `count` elementu z iteratora `first` .  Brane pod uwagę tylko podczas rozpoznawania przeciążenia, gdy parametr szablonu `Extent` nie jest `dynamic_extent` . |
|`span(It first, End last)` | Konstruowanie zakresu od elementów w iterator `first` do momentu `last` osiągnięcia końca. Brane pod uwagę tylko podczas rozpoznawania przeciążenia, gdy parametr szablonu `Extent` nie jest `dynamic_extent` . `It` musi być `contiguous_iterator` .  |
|`span(array<T, N>& arr) noexcept;`<br /><br />`span(const array<T, N>& arr) noexcept;`<br /><br />`span(type_identity_t<element_type> (&arr)[N]) noexcept;` |  Zbuduj zakres od `N` elementów określonej tablicy. Brane pod uwagę tylko podczas rozpoznawania przeciążenia, gdy parametr szablonu `Extent` ma `dynamic_extent` wartość lub równa się `N` . |
|`span(R&& r)` |  Zbuduj zakres od zakresu. Jeśli parametr szablonu nie jest, uczestniczy tylko w występowaniu przeciążenia `Extent` `dynamic_extent` .|
|`span(const span& other)` |  Konstruktor kopiujący wygenerowany przez kompilator. Skrócona kopia wskaźnika danych jest bezpieczna, ponieważ zakres nie przydziela pamięci do przechowywania elementów. |
|`span(const span<OtherElementType, OtherExtent>& s) noexcept;` | Konstruktor konwersji: konstruowanie zakresu z innego zakresu. Występuje tylko w przypadku, gdy parametr szablonu ma wartość lub `Extent` `dynamic_extent` `N` `dynamic_extent` równa się `Extent` .|

### <a name="example"></a>Przykład

```cpp
#include <span>

using namespace std;

int main()
{
    const int MAX=10;

    int x[MAX];
    for (int i = 0; i < MAX; i++)
    {
        x[i] = i;
    }

    span<int, MAX> span1{ x }; // fixed-size span: compiler error if size of x doesn't match template argument MAX
    span<int> span2{ x }; // size is inferred from x
    span<const int> span3 = span2; // converting constructor
    span<int> span4( span2 ); // copy constructor
}
```

## <a name="spansubspan"></a><a name="sub_view"></a> `span::subspan`

Pobierz Podzakres tego zakresu.

```cpp
constexpr auto subspan(size_type offset, size_type count = dynamic_extent) const noexcept;

template <size_t offset, size_t count = dynamic_extent>
constexpr auto subspan() const noexcept
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów, które mają zostać umieszczone w przedziale. Jeśli `count` jest `dynamic_extent` (wartość domyślna), Podzakres jest pobierany z `offset` do końca tego zakresu.

*Przesunięcie*\
Lokalizacja w tym zakresie, aby uruchomić Podzakres.

### <a name="return-value"></a>Wartość zwracana

Zakres rozpoczynający `offset` się w tym zakresie. Zawiera `count` elementy.

### <a name="remarks"></a>Uwagi

Dostępna jest wersja szablonu tej funkcji, która sprawdza liczbę w czasie kompilacji, która zachowuje informacje o zakresie przez zwrócenie zakresu z ustalonym zakresem.

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    cout << "mySpan.subspan(1,2): ";
    for (auto& i : mySpan.subspan(1,2))
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1,2>: ";
    for (auto& i : mySpan.subspan<1,2>())
    {
        cout << i;
    }
    cout << "\nmySpan.subspan<1>: ";
    for (auto& i : mySpan.subspan<1>)
    {
        cout << i;
    }
}
```

```Output
mySpan.subspan(1,2): 12
mySpan.subspan<1,2>: 12
mySpan.subspan<1>: 12
```

## <a name="spanvalue_type"></a><a name="value_type"></a> `span::value_type`

Typ elementu w zakresie, bez **`const`** ani **`volatile`** kwalifikacji.

```cpp
using value_type = std::remove_cv_t<T>;
```

### <a name="example"></a>Przykład

```cpp
#include <span>
#include <iostream>

using namespace std;

int main()
{
    int a[] = { 0,1,2 };
    span<int> mySpan(a);

    span<int>::value_type vType = mySpan[2];
    cout << vType;
}
```

```Output
2
```

## <a name="deduction-guides"></a><a name="deduction_guides"></a> Wskazówki dotyczące odejmowania

Poniższe przewodniki dotyczące odejmowania są dostępne dla zakresu.

```cpp
// Allows the extent to be deduced from std::array and C++ built-in arrays

template <class T, size_t Extent>
span(T (&)[Extent]) -> span<T, Extent>;

template <class T, size_t Size>
span(array<T, Size>&) -> span<T, Size>;

template <class T, size_t Size>
span(const array<T, Size>&) -> span<const T, Size>;

// Allows the element type to be deduced from the iterator and the end of the span.
// The iterator must be contiguous

template <contiguous_iterator It, class End>
span(It, End) -> span<remove_reference_t<iter_reference_t<It>>>;

// Allows the element type to be deduced from a range.
// The range must be contiguous

template <ranges::contiguous_range Rng>
span(Rng &&) -> span<remove_reference_t<ranges::range_reference_t<Rng>>>;
```

## <a name="see-also"></a>Zobacz także

[\<span>](../standard-library/span.md)  
[Jak używać odliczania argumentów szablonu klasy](https://devblogs.microsoft.com/cppblog/how-to-use-class-template-argument-deduction/)
