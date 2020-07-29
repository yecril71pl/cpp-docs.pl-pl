---
title: Klasa basic_string_view
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 6609f8e8ee8ccb0d14dbdf11cefc29f4b0dfa6f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219186"
---
# <a name="basic_string_view-class"></a>Klasa basic_string_view

Szablon klasy `basic_string_view<charT>` został dodany w języku c++ 17, aby służyć jako bezpieczny i wydajny sposób, aby funkcja akceptowała różne niepowiązane typy ciągów bez funkcji, która nie powinna być szablonowana na tych typach. Klasa przechowuje wskaźnik niebędący właścicielem do ciągłej sekwencji danych znakowych i długość określającą liczbę znaków w sekwencji. Nie wprowadzono żadnych założeń w odniesieniu do tego, czy sekwencja jest zakończona wartością null.

Standardowa biblioteka definiuje kilka specjalizacji na podstawie typu elementów:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

W tym dokumencie termin "string_view" odwołuje się ogólnie do któregokolwiek z tych definicji typów.

String_view opisuje minimalny typowy interfejs niezbędny do odczytu danych ciągu. Zapewnia stałą dostęp do danych źródłowych; nie tworzy żadnych kopii (z wyjątkiem `copy` funkcji). Dane mogą lub nie mogą zawierać wartości null (' \ 0 ') w dowolnym miejscu. String_view nie ma kontroli nad okresem istnienia obiektu. Jest odpowiedzialny za obiekt wywołujący, aby upewnić się, że dane ciągu bazowego są prawidłowe.

Funkcja, która akceptuje parametr typu string_view, może działać z dowolnym typem podobnym do ciągu, bez konieczności wykonywania funkcji do szablonu lub ograniczając funkcję do określonego podzestawu typów ciągów. Jedynym wymaganiem jest, że niejawna konwersja istnieje z typu ciągu do string_view. Wszystkie standardowe typy ciągów są niejawnie konwertowane na string_view, które zawierają ten sam typ elementu. Innymi słowy, `std::string` jest konwertowany na, `string_view` ale nie do `wstring_view` .

Poniższy przykład pokazuje funkcję niebędącą szablonem `f` , która przyjmuje parametr typu `wstring_view` . Może być wywoływana z argumentami typu `std::wstring` , `wchar_t*` , i `winrt::hstring` .

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ znaków, które są przechowywane w string_view. Standardowa biblioteka języka C++ zawiera następujące elementy typedef dla specjalizacji tego szablonu.

- [string_view](../standard-library/string-view-typedefs.md#string_view) dla elementów typu**`char`**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), dla**`wchar_t`**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) dla**`char16_t`**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **`char32_t`** .

*Cech*\
Wartość domyślna to [char_traits](char-traits-struct.md) < *CharType*>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_string_view](#basic_string_view)|Konstruuje string_view, która jest pusta lub w innym przypadku wskazuje wszystkie lub część danych innych obiektów ciągu lub tablicę znaków w stylu języka C.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|**const_iterator**|Iterator dostępu swobodnego, który może odczytywać **`const`** elementy.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**odwoła**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operatory elementów członkowskich

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje string_view lub przekonwertowany obiekt ciągu do innego string_view.|
|[operator\[\]](#op_at)|Zwraca element o określonym indeksie.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[w](#at)|Zwraca const_reference do elementu w określonej lokalizacji.|
|[Wstecz](#back)|Zwraca const_reference do ostatniego elementu.|
|[zaczną](#begin)|Zwraca iterator const odnoszący się do pierwszego elementu. (string_views są niemodyfikowalne).|
|[cbegin](#cbegin)|Tak samo jak [początek](#begin).|
|[cend](#cend)|Zwraca iterator const, który wskazuje jeden poza ostatnim elementem.|
|[kopiowane](#copy)|Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w string_view źródłowej do docelowej tablicy znaków. (Niezalecane. Użyj zamiast tego _Copy_s.)|
|[_Copy_s](#_copy_s)|Bezpieczna funkcja kopiowania CRT.|
|[porównaniu](#compare)|Porównuje string_view z określonym string_view, aby określić, czy są równe, czy też jest lexicographically mniejsze niż inne.|
|[crbegin —](#crbegin)|Analogicznie jak [rbegin](#rbegin).|
|[crend](#crend)|Analogicznie jak [rend](#rend).|
|[data](#data)|Zwraca nieprzetworzony wskaźnik niebędący właścicielem do sekwencji znaków.|
|[puste](#empty)|Sprawdza, czy string_view zawiera znaki.|
|[punktów](#end)|Analogicznie jak [cend](#cend).|
|[find](#find)|Wyszukuje w kierunku do przodu pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[find_first_not_of](#find_first_not_of)|Wyszukuje pierwszy znak, który nie jest elementem określonego string_view lub obiektu ciągu konwertowanego.|
|[find_first_of](#find_first_of)|Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego string_view lub konwertowanego obiektu ciągu.|
|[find_last_not_of](#find_last_not_of)|Wyszukuje ostatni znak, który nie jest elementem określonego string_view lub obiektu ciągu konwertowanego.|
|[find_last_of](#find_last_of)|Wyszukuje ostatni znak, który jest elementem określonego string_view lub konwertowanego obiektu ciągu.|
|[FSB](#front)|Zwraca const_reference do pierwszego elementu.|
|[Długość](#length)|Zwraca bieżącą liczbę elementów.|
|[max_size](#max_size)|Zwraca maksymalną liczbę znaków, jaką może zawierać string_view.|
|[rbegin](#rbegin)|Zwraca iterator const, który odnosi się do pierwszego elementu w odwróconej string_view.|
|[remove_prefix](#remove_prefix)|Przesuwa wskaźnik do przodu o określoną liczbę elementów.|
|[remove_suffix](#remove_suffix)|Zmniejsza rozmiar widoku o określoną liczbę elementów rozpoczynając od tyłu.|
|[rend](#rend)|Zwraca iterator const, który wskazuje na jeden ostatni element w odwróconym string_view.|
|[rfind](#rfind)|Wyszukuje string_view w odwrocie od pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[zmienia](#size)|Zwraca bieżącą liczbę elementów.|
|[substr —](#substr)|Zwraca podciąg o określonej długości, zaczynając od określonego indeksu.|
|[wymiany](#swap)|Wymiana zawartości dwóch string_views.|

## <a name="remarks"></a>Uwagi

Jeśli zostanie wyświetlona prośba o wygenerowanie sekwencji dłuższej niż [max_size](#max_size) elementów, funkcja zgłasza błąd długości przez wygenerowanie obiektu typu [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Wymagania

[std: c++ 17](../build/reference/std-specify-language-standard-version.md) lub nowsza

**Nagłówek:**\<string_view>

**Przestrzeń nazw:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view:: at

Zwraca const_reference do znaku w określonym indeksie równym 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks elementu, do którego ma zostać utworzone odwołanie.

### <a name="return-value"></a>Wartość zwracana

Const_reference znaku w położeniu określonym przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a następujące elementy są indeksowane po kolei przez dodatnie liczby całkowite, tak że string_view o długości *n* ma *n*% elementów indeksowanych przez liczbę *n-* 1. **w** przypadku zgłasza wyjątek dla nieprawidłowych indeksów, [operator \[ \] ](#op_at)w przeciwieństwie do.

Ogólnie rzecz biorąc zalecamy, aby **w** przypadku sekwencji, takich jak `std::vector` i string_view nie były nigdy używane. Nieprawidłowy indeks przeszedł do sekwencji jest błędem logiki, który powinien zostać odnaleziony i rozwiązany podczas opracowywania. Jeśli program nie ma absolutnej pewności, że jego indeksy są prawidłowe, należy je przetestować, nie wywoływać w () i polegać na wyjątkach w celu obrony przed programowaniem nieostrożnej.

Aby uzyskać więcej informacji, zobacz [basic_string_view:: operator \[ \] ](#op_at) .

### <a name="example"></a>Przykład

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view:: Back

Zwraca const_reference do ostatniego elementu.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference do ostatniego elementu w string_view.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusty.

Należy pamiętać, że po zmodyfikowaniu string_view, na przykład przez wywołanie `remove_suffix` , element zwracany przez tę funkcję nie jest już ostatnim elementem w danych źródłowych.

### <a name="example"></a>Przykład

String_view, który jest zbudowany za pomocą literału ciągu języka C, nie zawiera kończącej wartości null i w związku z tym w poniższym przykładzie `back` zwraca wartość "p", a nie "\ 0".

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Osadzone wartości null są traktowane jak każdy inny znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view:: basic_string_view

Konstruuje string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

*str*\
Wskaźnik do wartości znakowych.

*Funkcja*\
Liczba znaków do uwzględnienia w widoku.

## <a name="remarks"></a>Uwagi

Konstruktory z wykresem * parametr zakłada, że dane wejściowe są zakończone wartością null, ale kończący wartość null nie jest uwzględniona w string_view.

Możesz również skonstruować string_view za pomocą literału. Zobacz [operator "" OHR](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view:: BEGIN

Analogicznie jak [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_iterator odnoszący się do pierwszego elementu.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view:: cbegin

Zwraca const_iterator, która odnosi się do pierwszego elementu w zakresie.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu `cbegin() == cend()` ).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view:: cend

Zwraca const_iterator, która odnosi się do lokalizacji tylko poza ostatnim elementem w zakresie.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`const`** Iterator dostępu swobodnego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

Nie można usunąć odwołania do wartości zwracanej przez `cend` .

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view:: Compare

Wykonuje porównanie z uwzględnieniem wielkości liter z określonym string_view (lub typem ciągu konwertowanego), aby określić, czy dwa obiekty są równe lub czy nie są lexicographically mniejsze od siebie. [ \<string_view> Operatory](string-view-operators.md) używają tej funkcji elementu członkowskiego do wykonywania porównań.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parametry

*strv*\
String_view, które mają być porównane z tym string_view.

*Terminal*\
Indeks tego string_view, w którym rozpoczyna się porównywanie.

*numerowan*\
Maksymalna liczba znaków z tego string_view, które mają być porównywane.

*num2*\
Maksymalna liczba znaków z *Strv* , które mają być porównywane.

*Przesunięcie*\
Indeks *Strv* , w którym rozpoczyna się porównanie.

*PTR*\
Ciąg języka C, który ma zostać porównany z tym string_view.

### <a name="return-value"></a>Wartość zwracana

Wartość ujemna, jeśli ta string_view jest mniejsza niż *Strv* lub *PTR*; zero, jeśli dwie sekwencje znaków są równe; lub wartość dodatnia, jeśli ten string_view jest większy niż *Strv* lub *PTR*.

### <a name="remarks"></a>Uwagi

`compare`Funkcja członkowska wykonuje porównanie z uwzględnieniem wielkości liter wszystkich lub części każdej sekwencji znaków.

### <a name="example"></a>Przykład

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view:: Copy

Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w string_view źródłowej do docelowej tablicy znaków. Zalecamy używanie funkcji Secure [basic_string_view:: _Copy_s](#_copy_s) .

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*PTR*\
Docelowa tablica znaków, do której mają zostać skopiowane elementy.

*liczbą*\
Liczba znaków, które mają być skopiowane, z string_view źródłowej.

*Przesunięcie*\
Pozycja początkowa w string_view źródłowym, z której mają zostać wykonane kopie.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view:: _Copy_s

Zabezpiecz funkcję kopiowania CRT, która ma być używana zamiast [kopiowania](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*dest*\
Docelowa tablica znaków, do której mają zostać skopiowane elementy.

*dest_size*\
Rozmiar miejsca *docelowego*.

_ *Zliczanie* znaków, które mają być skopiowane, z ciągu źródłowego.

*_Off*\
Pozycja początkowa w ciągu źródłowym, z którego mają zostać wykonane kopie.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

Aby uzyskać więcej informacji, zobacz [c-Runtime-Library/Security-features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view:: crbegin —

Zwraca const_reverse_iterator, który odnosi się do pierwszego elementu w odwróconej string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Const_reverse_iterator, który odnosi się do pierwszego elementu w odwróconej string_view.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view:: crend

Analogicznie jak [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_reverse_iterator, która odnosi się do jednej poza końcem odwróconej string_view.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::d ATA

Zwraca nieprzetworzony wskaźnik niebędący właścicielem do sekwencji znaków const obiektu, który został użyty do skonstruowania string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wartości stałej do pierwszego elementu sekwencji znaków.

### <a name="remarks"></a>Uwagi

Wskaźnik nie może modyfikować znaków.

Sekwencja string_view znaków nie musi być zakończona wartością null. Zwracany typ dla `data` nie jest prawidłowym ciągiem C, ponieważ nie dołączono żadnego znaku o wartości null. Znak null ' \ 0 ' nie ma specjalnego znaczenia w obiekcie typu string_view i może być częścią obiektu string_view podobnie jak każdy inny znak.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view:: Empty

Testuje, czy string_view zawiera znaki, czy nie.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt string_view nie zawiera żadnych znaków; **`false`** Jeśli zawiera co najmniej jeden znak.

### <a name="remarks"></a>Uwagi

Funkcja członkowska jest równoważna z [rozmiarem](#size)() = = 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view:: end

Zwraca const_iterator dostępu swobodnego, który wskazuje na jeden ostatni z ostatniego elementu.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_iterator dostępu swobodnego, który wskazuje na jeden ostatni z ostatniego elementu.

### <a name="remarks"></a>Uwagi

`end`służy do sprawdzania, czy const_iterator osiągnął koniec jego string_view. Nie można usunąć odwołania do wartości zwracanej przez `end` .

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view:: find

Wyszukuje string_view w kierunku do przodu pierwszego wystąpienia znaku lub podciągu, który odpowiada określonej sekwencji znaków.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, w którym rozpocznie się wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków w *PTR*, licząc od pierwszego znaku.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos` .

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view:: find_first_not_of

Wyszukuje pierwszy znak, który nie jest elementem określonego string_view lub obiektu ciągu konwertowanego.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, w którym rozpocznie się wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos` .

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view:: find_first_of

Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, w którym rozpocznie się wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos` .

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view:: find_last_not_of

Wyszukuje ostatni znak, który nie jest elementem określonego string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się zakończyć wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków, która jest odliczana od pierwszego znaku w *PTR*.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `string_view::npos` .

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view:: find_last_of

Wyszukuje ostatni znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się zakończyć wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku podciągu przeszukiwany po pomyślnym; w przeciwnym razie `npos` .

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view:: front

Zwraca const_reference do pierwszego elementu.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference do pierwszego elementu.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusty.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view:: length

Zwraca bieżącą liczbę elementów.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska jest taka sama jak [rozmiar](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view:: max_size

Zwraca maksymalną liczbę znaków, jaką może zawierać string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba znaków, jaką może zawierać string_view.

### <a name="remarks"></a>Uwagi

Wyjątek typu [length_error](../standard-library/length-error-class.md) jest generowany, gdy operacja generuje string_view o długości większej niż `max_size()` .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view:: operator =

Przypisuje string_view lub przekonwertowany obiekt ciągu do innego string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Przykład

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view:: operator []

Udostępnia const_reference znaku z określonym indeksem.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks elementu, do którego ma zostać utworzone odwołanie.

### <a name="return-value"></a>Wartość zwracana

Const_reference znaku w położeniu określonym przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a następujące elementy są indeksowane po kolei przez dodatnie liczby całkowite, tak że string_view o długości *n* ma *n*% elementów indeksowanych przez liczbę *n* -1.

`operator[]`jest szybsza niż funkcja członkowska [w](#at) celu zapewnienia dostępu do odczytu do elementów string_view.

`operator[]`nie sprawdza, czy indeks przeszedł jako argument jest prawidłowy. Nieprawidłowy indeks przeszedł do `operator[]` wyników w niezdefiniowanym zachowaniu.

Zwracane odwołanie może zostać unieważnione, jeśli dane ciągu bazowego są modyfikowane lub usuwane przez obiekt będący właścicielem.

Podczas kompilowania z [ \_ \_ \_ poziomem debugowania iteratora](../standard-library/iterator-debug-level.md) ustawionym na 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu poza granicami string_view. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view:: rbegin

Zwraca iterator const do pierwszego elementu w odwróconej string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator dostępu swobodnego do pierwszego elementu w odwróconej string_view, co może być ostatnim elementem w odpowiadającym mu nieodwróconym string_view.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconą string_view, tak jak [początek](#begin) jest używany z string_view. `rbegin`może służyć do inicjowania iteracji do tyłu.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view:: remove_prefix

Przesuwa wskaźnik do przodu o określoną liczbę elementów.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia dane bazowe bez zmian. Przenosi string_view wskaźnik do przodu o n elementów i ustawia prywatny `size` element członkowski danych na rozmiar-n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view:: remove_suffix

Zmniejsza rozmiar widoku o określoną liczbę elementów rozpoczynając od tyłu.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia dane bazowe i wskaźnik do niego bez zmian. Ustawia prywatny `size` element członkowski danych na wartość size-n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view:: rend

Zwraca iterator const, który wskazuje na jeden ostatni element w odwróconym string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator typu const odwrotnie, który wskazuje na jeden ostatni element w odwróconej string_view.

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconą string_view, tak jak [koniec](#end) jest używany z string_view. `rend`można go użyć do sprawdzenia, czy iterator odwrotny osiągnął koniec string_view. Nie można usunąć odwołania do wartości zwracanej przez `rend` .

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view:: rfind

Wyszukuje string_view w odwrocie dla podciągu, który pasuje do określonej sekwencji znaków.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

*Przesunięcie*\
Indeks, w którym rozpocznie się wyszukiwanie.

*PTR*\
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczbą*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
String_view, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągu w przypadku powodzenia; w przeciwnym razie `npos` .

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view:: size

Zwraca liczbę elementów w string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Długość string_view.

### <a name="remarks"></a>Uwagi

String_view może zmodyfikować jego długość, na przykład przez `remove_prefix` i `remove_suffix` . Ponieważ to nie modyfikuje bazowych danych ciągu, rozmiar string_view nie jest koniecznie rozmiarem danych źródłowych.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view:: substr

Zwraca string_view, która reprezentuje (najwyżej) określoną liczbę znaków z określonego położenia.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks lokalizowania elementu na pozycji, z której wykonano kopię, z wartością domyślną 0.

*liczbą*\
Liczba znaków do uwzględnienia w podciągu, jeśli są obecne.

### <a name="return-value"></a>Wartość zwracana

Obiekt string_view, który reprezentuje określoną podsekwencję elementów.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view:: swap

Wymienia dwa string_views, innymi słowy, wskaźniki do danych ciągu bazowego i wartości rozmiaru.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*OHR*\
Źródło string_view, którego wartości wskaźnika i rozmiaru mają być wymieniane z string_view docelowy.

## <a name="see-also"></a>Zobacz także

[\<string_view>](../standard-library/string-view.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
