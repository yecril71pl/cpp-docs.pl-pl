---
title: basic_string_view, klasa
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
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364892"
---
# <a name="basic_string_view-class"></a>basic_string_view, klasa

Szablon `basic_string_view<charT>` klasy został dodany w języku C++ 17 służyć jako bezpieczny i skuteczny sposób dla funkcji do akceptowania różnych niepowiązanych typów ciągów bez funkcji konieczności tworzenia szablonów na tych typach. Klasa posiada wskaźnik niebędący właścicielem do ciągłej sekwencji danych znaków i długość, która określa liczbę znaków w sekwencji. Nie przyjmuje się założenia w odniesieniu do tego, czy sekwencja jest zakończona zerem.

Biblioteka standardowa definiuje kilka specjalizacji na podstawie typu elementów:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

W tym dokumencie termin "string_view" odnosi się ogólnie do każdego z tych typedefs.

String_view opisuje minimalny wspólny interfejs niezbędny do odczytu danych ciągu. Zapewnia const dostęp do danych źródłowych; nie wykonuje żadnych kopii (z wyjątkiem `copy` funkcji). Dane mogą, ale nie mogą zawierać wartości null ('\0') w dowolnym miejscu. String_view nie ma kontroli nad okresem istnienia obiektu. Jest to odpowiedzialność wywołującego, aby upewnić się, że podstawowe dane ciągu jest prawidłowy.

Funkcja, która akceptuje parametr typu string_view może być wykonana do pracy z dowolnego typu podobnego do ciągu, bez podejmowania funkcji do szablonu lub ograniczając funkcję do określonego podzbioru typów ciągów. Jedynym wymaganiem jest, że istnieje niejawna konwersja od typu ciągu do string_view. Wszystkie standardowe typy ciągów są niejawnie konwertowane na string_view, który zawiera ten sam typ elementu. Innymi słowy, `std::string` a jest wymienialny `string_view` na, `wstring_view`ale nie na .

W poniższym przykładzie przedstawiono funkcję `f` niebędącą `wstring_view`szablonem, która przyjmuje parametr typu . Można go wywołać z `std::wstring` `wchar_t*`argumentami `winrt::hstring`typu , i .

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

*Chartype*\
Typ znaków, które są przechowywane w string_view. Standardowa biblioteka języka C++ zawiera następujące typedefs dla specjalizacji tego szablonu.

- [string_view](../standard-library/string-view-typedefs.md#string_view) dla elementów typu **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), dla **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) **dla char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) dla **char32_t**.

*Cechy*\
Domyślnie [char_traits>](char-traits-struct.md)<*chartype.*

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_string_view](#basic_string_view)|Konstruuje string_view, który jest pusty lub wskazuje na całość lub część danych innego obiektu ciągu lub tablicy znaków w stylu C.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|**const_iterator**|Iterator dostępu losowego, który może odczytywać **const** elementów.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**Const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Sterująca**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**Odwołanie**|`using reference = value_type&;`|
|**Reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operatorzy członkowskie

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje obiekt string_view lub konwertowany do innego string_view.|
|[Operator\[\]](#op_at)|Zwraca element w określonym indeksie.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[O](#at)|Zwraca const_reference do elementu w określonej lokalizacji.|
|[Wstecz](#back)|Zwraca const_reference do ostatniego elementu.|
|[Rozpocząć](#begin)|Zwraca iterator konstacyjny adresowania pierwszego elementu. (string_views są niezmienne.)|
|[cbegin ( cbegin )](#cbegin)|Tak samo jak [na początku](#begin).|
|[cend](#cend)|Zwraca iterator const, który wskazuje jeden przeszłości ostatniego elementu.|
|[Kopii](#copy)|Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanego w źródle string_view do docelowej tablicy znaków. (Nie zalecane. Zamiast tego użyj _Copy_s).)|
|[_Copy_s](#_copy_s)|Bezpieczna funkcja kopiowania CRT.|
|[Porównać](#compare)|Porównuje string_view z określonym string_view, aby ustalić, czy są one równe lub jeśli jeden jest leksykograficznie mniej niż inne.|
|[Crbegin](#crbegin)|Tak samo jak [rbegin](#rbegin).|
|[Crend](#crend)|Tak samo jak [rend](#rend).|
|[Danych](#data)|Zwraca nieprzetworzony wskaźnik niebędący właścicielem do sekwencji znaków.|
|[Pusty](#empty)|Sprawdza, czy string_view zawiera znaki.|
|[Końcu](#end)|Tak samo jak [cend](#cend).|
|[find](#find)|Wyszukuje w kierunku do przodu dla pierwszego wystąpienia podciąg, który pasuje do określonej sekwencji znaków.|
|[find_first_not_of](#find_first_not_of)|Wyszukuje pierwszy znak, który nie jest żadnym elementem określonego obiektu string_view lub konwertowego ciągu.|
|[find_first_of](#find_first_of)|Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego obiektu string_view lub konwersalnej.|
|[find_last_not_of](#find_last_not_of)|Wyszukuje ostatni znak, który nie jest żadnym elementem określonego obiektu string_view lub konwertowego ciągu.|
|[find_last_of](#find_last_of)|Wyszukuje ostatni znak, który jest elementem określonego obiektu string_view lub konwertowego ciągu.|
|[Przednie](#front)|Zwraca const_reference do pierwszego elementu.|
|[Długość](#length)|Zwraca bieżącą liczbę elementów.|
|[Max_size](#max_size)|Zwraca maksymalną liczbę znaków, które może zawierać string_view.|
|[rbegin (rbegin)](#rbegin)|Zwraca iterator konspiratora, który odnosi się do pierwszego elementu w odwróconym string_view.|
|[remove_prefix](#remove_prefix)|Przesuwa wskaźnik do przodu o określoną liczbę elementów.|
|[remove_suffix](#remove_suffix)|Zmniejsza rozmiar widoku o określoną liczbę elementów, począwszy od tyłu.|
|[Rend](#rend)|Zwraca iterator const, który wskazuje jeden obok ostatniego elementu w odwróconym string_view.|
|[rfind (rfind)](#rfind)|Przeszukuje string_view w odwrotnej kolejności dla pierwszego wystąpienia podciąg, który pasuje do określonej sekwencji znaków.|
|[Rozmiar](#size)|Zwraca bieżącą liczbę elementów.|
|[podstr](#substr)|Zwraca podciąg o określonej długości, zaczynając od określonego indeksu.|
|[Wymiany](#swap)|Wymiana zawartości dwóch string_views.|

## <a name="remarks"></a>Uwagi

Jeśli funkcja jest proszona o wygenerowanie sekwencji dłuższej niż [max_size](#max_size) elementów, funkcja zgłasza błąd długości, rzucając obiekt typu [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Wymagania

[std:c++17](../build/reference/std-specify-language-standard-version.md) lub nowsze

**Nagłówek:** \<string_view>

**Przestrzeń nazw:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view::w

Zwraca const_reference do znaku w określonym indeksie opartym na 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks elementu, do którego ma się odwoływać.

### <a name="return-value"></a>Wartość zwracana

Const_reference do znaku w pozycji określonej przez indeks parametrów.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a następujące elementy są indeksowane kolejno przez dodatnie liczby całkowite, tak aby string_view długości *n* ma *n*th element indeksowany przez liczbę *n -* 1. **w** yrzuca wyjątek dla nieprawidłowych indeksów, w przeciwieństwie do [operatora\[](#op_at).

Ogólnie rzecz biorąc **at** zaleca się, że `std::vector` w dla sekwencji, takich jak i string_view nigdy nie powinny być używane. Nieprawidłowy indeks przekazany do sekwencji jest błąd logiczny, który powinien zostać wykryty i naprawiony podczas programowania. Jeśli program nie jest absolutnie pewien, że jego indeksy są prawidłowe, należy przetestować je, a nie wywołać at() i polegać na wyjątkach, aby bronić się przed nieostrożnym programowaniem.

Zobacz [basic_string_view::operator,\[ aby](#op_at) uzyskać więcej informacji.

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view::powrót

Zwraca const_reference do ostatniego elementu.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference do ostatniego elementu w string_view.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusta.

Należy pamiętać, że po string_view jest modyfikowany, `remove_suffix`na przykład przez wywołanie , a następnie element zwrócony przez tę funkcję nie jest już ostatnim elementem w danych źródłowych.

### <a name="example"></a>Przykład

A string_view, który jest skonstruowany z literałem ciągu C nie zawiera kończące `back` się null i dlatego w poniższym przykładzie zwraca "p", a nie "\0".

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Osadzone wartości null są traktowane jako każdy inny znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view::basic_string_view

Konstruuje string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

*Str*\
Wskaźnik do wartości znaków.

*len*\
Liczba znaków do uwzględnienia w widoku.

## <a name="remarks"></a>Uwagi

Konstruktory z charT* parametr zakłada, że dane wejściowe jest zakończone zerem, ale kończące się null nie jest uwzględniony w string_view.

Można również skonstruować string_view za pomocą literału. Zobacz [operator""sv](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view::begin

Tak samo jak [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_iterator adresowania pierwszego elementu.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

Zwraca const_iterator, który odnosi się do pierwszego elementu w zakresie.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu losowego, który wskazuje pierwszy element zakresu lub lokalizację tuż za końcem pustego zakresu (dla pustego **const** `cbegin() == cend()`zakresu).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cend

Zwraca const_iterator, który odnosi się do lokalizacji tuż poza ostatnim elementem w zakresie.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**Const** iterator dostępu losowego, który wskazuje tuż za końcem zakresu.

### <a name="remarks"></a>Uwagi

Wartość zwrócona `cend` przez nie powinny być wyłuskiwane.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view::porównaj

Wykonuje porównanie z uwzględnieniem wielkości liter z określonym string_view (lub typu ciągu konwersalnej), aby określić, czy dwa obiekty są równe lub jeśli jeden jest leksykograficznie mniejszy od drugiego. Operatory string_view [ \<>](string-view-operators.md) używają tej funkcji elementu członkowskiego do przeprowadzania porównań.

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
String_view, które należy porównać do tego string_view.

*Poz*\
Indeks tego string_view, od którego rozpoczyna się porównanie.

*Num*\
Maksymalna liczba znaków z tego string_view do porównania.

*num2*\
Maksymalna liczba znaków z *strv* do porównania.

*Przesunięcie*\
Indeks *strv,* od którego rozpoczyna się porównanie.

*Ptr*\
Ciąg C, który ma być porównywany z tym string_view.

### <a name="return-value"></a>Wartość zwracana

Wartość ujemna, jeśli ta string_view jest mniejsza niż *strv* lub *ptr;* zero, jeśli dwie sekwencje znaków są równe; lub wartość dodatnią, jeśli string_view jest większa niż *strv* lub *ptr*.

### <a name="remarks"></a>Uwagi

Funkcje `compare` członkowskie wykonują porównanie z uwzględnieniem wielkości liter wszystkich lub części każdej sekwencji znaków.

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view::copy

Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanego w źródle string_view do docelowej tablicy znaków. Zamiast tego zaleca się używanie funkcji secure [basic_string_view::_Copy_s.](#_copy_s)

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Ptr*\
Docelowa tablica znaków, do której elementy mają być kopiowane.

*Liczba*\
Liczba znaków, które mają być kopiowane co najwyżej ze źródła string_view.

*Przesunięcie*\
Pozycja początkowa w string_view źródłowym, z którego mają być wykonane kopie.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie skopiowanych.

### <a name="remarks"></a>Uwagi

Znak zerowy nie jest dołączany na końcu kopii.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view::_Copy_s

Bezpieczna funkcja kopiowania CRT do użycia zamiast [kopiowania](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*Dest*\
Docelowa tablica znaków, do której elementy mają być kopiowane.

*dest_size*\
Wielkość *dest*.

_ *Count* Liczba znaków, które mają być kopiowane, co najwyżej z ciągu źródłowego.

*_off*\
Pozycja początkowa w ciągu źródłowym, z którego mają być wykonane kopie.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie skopiowanych.

### <a name="remarks"></a>Uwagi

Znak zerowy nie jest dołączany na końcu kopii.

Aby uzyskać więcej informacji, zobacz [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view::crbegin

Zwraca const_reverse_iterator, który odnosi się do pierwszego elementu w odwróconym string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Const_reverse_iterator, który rozwiązuje pierwszy element w odwróconym string_view.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view::crend

Tak samo jak [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_reverse_iterator, która zajmuje się jednym poza końcem odwróconego string_view.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::data

Zwraca nieprzetworzony wskaźnik niebędący właścicielem do sekwencji znaków const obiektu, który został użyty do skonstruowania string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do const do pierwszego elementu sekwencji znaków.

### <a name="remarks"></a>Uwagi

Wskaźnik nie może modyfikować znaków.

Sekwencja znaków string_view nie musi być zakończona z wartością null. Typ zwracany `data` dla nie jest prawidłowy ciąg C, ponieważ nie znak null pobiera dołączane. Znak null "\0" nie ma specjalnego znaczenia w obiekcie typu string_view i może być częścią obiektu string_view, tak jak każdy inny znak.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::empty

Sprawdza, czy string_view zawiera znaki, czy nie.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekt string_view nie zawiera żadnych znaków; **false,** jeśli ma co najmniej jeden znak.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego jest równoważna [rozmiarowi](#size)() == 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view::end

Zwraca const_iterator dostępu losowego, który wskazuje jeden przeszłości ostatniego elementu.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_iterator dostępu losowego, który wskazuje jeden przeszłości ostatniego elementu.

### <a name="remarks"></a>Uwagi

`end`służy do sprawdzenia, czy const_iterator osiągnął koniec string_view. Wartość zwrócona `end` przez nie powinny być wyłuskiwane.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view::znajdź

Przeszukuje string_view w kierunku do przodu w celu pierwszego wystąpienia znaku lub podciągów, który pasuje do określonej sekwencji znaków.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się rozpocząć wyszukiwanie.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków w *ptr*, licząc do przodu od pierwszego znaku.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągów wyszukiwany po pomyślnym; w `npos`przeciwnym razie .

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view::find_first_not_of

Wyszukuje pierwszy znak, który nie jest elementem określonego obiektu string_view lub konwertowego ciągu.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się rozpocząć wyszukiwanie.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków, licząc do przodu od pierwszego znaku, w ciągu C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągów wyszukiwany po pomyślnym; w `npos`przeciwnym razie .

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view::find_first_of

Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się rozpocząć wyszukiwanie.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków, licząc do przodu od pierwszego znaku, w ciągu C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągów wyszukiwany po pomyślnym; w `npos`przeciwnym razie .

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view::find_last_not_of

Wyszukuje ostatni znak, który nie jest żadnym elementem określonego string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, przy którym wyszukiwanie ma się zakończyć.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków, licząc do przodu od pierwszego znaku, w *ptr*.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągów wyszukiwany po pomyślnym; w `string_view::npos`przeciwnym razie .

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

Wyszukuje ostatni znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, przy którym wyszukiwanie ma się zakończyć.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków, licząc do przodu od pierwszego znaku, w ciągu C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku podciągów wyszukiwany po pomyślnym; w `npos`przeciwnym razie .

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view::przód

Zwraca const_reference do pierwszego elementu.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference do pierwszego elementu.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusta.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view::długość

Zwraca bieżącą liczbę elementów.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego jest taka sama jak [rozmiar](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

Zwraca maksymalną liczbę znaków, które może zawierać string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba znaków, które może zawierać string_view.

### <a name="remarks"></a>Uwagi

Wyjątek [typu length_error](../standard-library/length-error-class.md) jest zgłaszany, gdy operacja tworzy string_view o długości `max_size()`większej niż .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::operator=

Przypisuje obiekt string_view lub konwertowany do innego string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Przykład

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view::operator[]

Zawiera const_reference do znaku z określonym indeksem.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks elementu, do którego ma się odwoływać.

### <a name="return-value"></a>Wartość zwracana

Const_reference do znaku w pozycji określonej przez indeks parametrów.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a następujące elementy są indeksowane kolejno przez dodatnie liczby całkowite, tak aby string_view długości *n* ma *n*th element indeksowany przez liczbę *n* - 1.

`operator[]`jest szybszy niż [funkcja](#at) elementu członkowskiego w celu zapewnienia dostępu do odczytu do elementów string_view.

`operator[]`nie sprawdza, czy indeks przekazany jako argument jest prawidłowy. Nieprawidłowy indeks `operator[]` przekazany do wyników w niezdefiniowanym zachowaniu.

Odwołanie zwrócone może zostać unieważnione, jeśli podstawowe dane ciągu są modyfikowane lub usuwane przez obiekt własny.

Podczas kompilowania z [ \_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) ustawiona na 1 lub 2, błąd środowiska uruchomieniowego wystąpi, jeśli spróbujesz uzyskać dostęp do elementu poza granicami string_view. Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view::rbegin

Zwraca iteratora konspiratora do pierwszego elementu w odwróconym string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca iteratora dostępu losowego do pierwszego elementu w odwróconym string_view, adresując, co byłoby ostatnim elementem w odpowiednich niezwróconych string_view.

### <a name="remarks"></a>Uwagi

`rbegin`jest używany z odwróconym string_view tak jak [begin](#begin) jest używany z string_view. `rbegin`może służyć do inicjowania iteracji do tyłu.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view::remove_prefix

Przesuwa wskaźnik do przodu o określoną liczbę elementów.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia dane bazowe bez zmian. Przenosi wskaźnik string_view do przodu przez n elementów i ustawia element członkowski danych prywatnych `size` do rozmiaru - n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view::remove_suffix

Zmniejsza rozmiar widoku o określoną liczbę elementów, począwszy od tyłu.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia dane źródłowe i wskaźnik do niego bez zmian. Ustawia prywatny `size` element członkowski danych na rozmiar - n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view::rend

Zwraca iterator const, który wskazuje jeden obok ostatniego elementu w odwróconym string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Const odwrotnej odwrotnej dostępu iteratora, który wskazuje na jeden przeszłości ostatni element w odwróconej string_view.

### <a name="remarks"></a>Uwagi

`rend`jest używany z odwróconym string_view tak jak [koniec](#end) jest używany z string_view. `rend`można użyć do sprawdzenia, czy odwrotny iterator osiągnął koniec string_view. Wartość zwrócona `rend` przez nie powinny być wyłuskiwane.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view::rfind

Przeszukuje string_view w odwrotnej kolejności podciąg, który pasuje do określonej sekwencji znaków.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal (ł.*\
Wartość znaku, dla której funkcja elementu członkowskiego ma być wyszukiwana.

*Przesunięcie*\
Indeks, od którego ma się rozpocząć wyszukiwanie.

*Ptr*\
Ciąg C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Liczba*\
Liczba znaków, licząc do przodu od pierwszego znaku, w ciągu C, dla którego funkcja elementu członkowskiego jest do wyszukiwania.

*Str*\
string_view, dla którego funkcja elementu członkowskiego ma wyszukiwać.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciągów po pomyślnym; w `npos`przeciwnym razie .

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view::size

Zwraca liczbę elementów w string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Długość string_view.

### <a name="remarks"></a>Uwagi

String_view może modyfikować jego długość, `remove_prefix` na `remove_suffix`przykład przez i . Ponieważ nie modyfikuje to podstawowych danych ciągu, rozmiar string_view niekoniecznie jest rozmiarem danych źródłowych.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::podstr

Zwraca string_view, która reprezentuje (co najwyżej) określoną liczbę znaków z określonej pozycji.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
Indeks lokalizujący element w pozycji, z której wykonana jest kopia, z domyślną wartością 0.

*Liczba*\
Liczba znaków do uwzględnienia w podciąg, jeśli są one obecne.

### <a name="return-value"></a>Wartość zwracana

Obiekt string_view reprezentujący określoną podsekwencji elementów.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::swap

Wymienia dwa string_views, innymi słowy wskaźniki do podstawowych danych ciągu i wartości rozmiaru.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*Sv*\
Źródło string_view którego wartości wskaźnika i rozmiaru mają być wymieniane z wartością docelową string_view.

## <a name="see-also"></a>Zobacz też

[\<string_view>](../standard-library/string-view.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
