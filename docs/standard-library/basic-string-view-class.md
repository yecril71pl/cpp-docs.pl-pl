---
title: basic_string_view klasy
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
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346636"
---
# <a name="basicstringview-class"></a>basic_string_view klasy

Szablon klasy `basic_string_view<charT>` został dodany w języku C ++ 17, które będzie służyć jako bezpieczny i skuteczny sposób dla funkcji zaakceptować różnych typów ciągów niezwiązanych ze sobą bez funkcji konieczności jest szablonowana na tych typów. Klasa przechowuje wskaźnik nie będący właścicielem ciągłej sekwencji danych znakowych i długości, która określa liczbę znaków w sekwencji. Nie założeń składa się w odniesieniu do tego, czy sekwencja jest zakończony znakiem null.

Standardowa biblioteka definiuje kilka specjalizacje oparte na typ elementów:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

W tym dokumencie termin "string_view" odnosi się zazwyczaj do dowolnego z tych definicji typów.

String_view opisano minimalną wspólny interfejs niezbędne do odczytu danych ciągu. Zapewnia ona const dostęp do danych bazowych; to sprawia, że nie kopie (z wyjątkiem `copy` funkcji). Dane mogą lub nie może zawierać wartości null ('\0') w dowolnym położeniu. String_view nie ma kontroli nad okresem istnienia obiektu. Odpowiada za wywołującego upewnij się, że danych bazowych ciągu jest prawidłowy.

Funkcja, która akceptuje parametr typu string_view będzie możliwe do pracy z dowolnego typu przypominającego ciąg bez wprowadzania funkcji do szablonu lub ograniczając funkcji do konkretnego podzbioru typów ciągów. Jedynym wymaganiem jest, że istnieje niejawna konwersja z typu string string_view. Wszystkie typy standardowego ciągu są niejawnie konwertowane na string_view, który zawiera ten sam typ elementu. Innymi słowy `std::string` jest konwertowany na `string_view` , ale nie `wstring_view`.

W poniższym przykładzie pokazano funkcję nieszablonowe `f` pobierającej parametr typu `wstring_view`. Może ona zostać wywołana z argumentami typu `std::wstring`, `wchar_t*`, i `winrt::hstring`.

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

*CharType*<br/>
Typ znaków, które są przechowywane w string_view. C++ Standardowa biblioteka zawiera poniższe definicje typów dla specjalizacji szablonu.
- [string_view](../standard-library/string-view-typedefs.md#string_view) dla elementów typu **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), aby uzyskać **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) dla **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) dla **char32_t**.

*Cechy*<br/>
Wartość domyślna to [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_string_view](#basic_string_view)|Tworzy string_view, która jest pusta lub — w przeciwnym razie punkty do całości lub części innego obiektu stringu firmy danych lub do tablicy znaków stylu C.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|**const_iterator**|Random dostępu swobodnego, który może odczytać **const** elementów.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**npos —**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**Odwołanie**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operatory elementów członkowskich

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje string_view lub przekonwertować obiekt ciągu do innego string_view.|
|[Operator\[\]](#op_at)|Zwraca element pod określonym indeksem.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[at](#at)|Zwraca const_reference do elementu w określonej lokalizacji.|
|[back](#back)|Const_reference — zwraca ostatni element.|
|[begin](#begin)|Zwraca iterator stałych adresujący pierwszy element. (string_views są niezmienne.)|
|[cbegin](#cbegin)|Taki sam jak [rozpocząć](#begin).|
|[cend](#cend)|Zwraca iterator const, który wskazuje na jednym elementem.|
|[Kopiuj](#copy)|Kopiuje co najwyżej określoną liczbę znaków z indeksowanej pozycji w string_view źródłowej do docelowej tablicy znaków. (Nie jest zalecane. _Copy_s — zamiast tego użyj.)|
|[_Copy_s](#_copy_s)|Zabezpiecz CRT funkcji kopiowania.|
|[compare](#compare)|Porównuje string_view przy użyciu określonego string_view, aby określić, czy są równe, lub jeśli jest leksykograficznie krótszy niż drugi.|
|[crbegin](#crbegin)|Taki sam jak [rbegin —](#rbegin).|
|[crend](#crend)|Taki sam jak [rend —](#rend).|
|[data](#data)|Zwraca surowy wskaźnik nie będący właścicielem sekwencję znaków.|
|[pusty](#empty)|Sprawdza, czy string_view zawiera znaki.|
|[koniec](#end)|Taki sam jak [cend](#cend).|
|[Znajdź](#find)|Wyszukiwanie w kierunku do przodu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[find_first_not_of](#find_first_not_of)|Wyszukuje pierwszy znak, który nie jest żadnym elementem określonego string_view lub przekonwertowania ciągu obiektu.|
|[find_first_of](#find_first_of)|Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego string_view lub przekonwertowania ciągu obiektu.|
|[find_last_not_of](#find_last_not_of)|Wyszukuje ostatni znak, który nie jest żadnym elementem określonego string_view lub przekonwertowania ciągu obiektu.|
|[find_last_of](#find_last_of)|Wyszukuje ostatni znak, który jest elementem określonego string_view lub przekonwertowania ciągu obiektu.|
|[Frontonu](#front)|Const_reference — zwraca pierwszy element.|
|[Długość](#length)|Zwraca aktualną liczbę elementów.|
|[max_size](#max_size)|Zwraca maksymalną liczbę znaków, które mogą zawierać string_view.|
|[rbegin](#rbegin)|Zwraca iterator const, który dotyczy pierwszego elementu w odwróconym string_view.|
|[remove_prefix](#remove_prefix)|Przesuwa wskaźnik myszy do przodu przez określoną liczbę elementów.|
|[remove_suffix](#remove_suffix)|Zmniejsza rozmiar widoku przez określoną liczbę elementów, poczynając od tyłu.|
|[rend](#rend)|Zwraca iterator const, który wskazuje na po ostatnim elemencie w odwróconej string_view.|
|[rfind —](#rfind)|Wyszukuje string_view w odwrotnej kolejności dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[Rozmiar](#size)|Zwraca aktualną liczbę elementów.|
|[substr](#substr)|Zwraca podciąg znaków o określonej długości, rozpoczynając od określonego indeksu.|
|[swap](#swap)|Wymiana zawartości dwóch string_views.|

## <a name="remarks"></a>Uwagi

Jeśli funkcja jest proszony o wygenerowanie sekwencji dłużej niż [max_size —](#max_size) elementów, funkcja zgłasza błąd długości, zwracając obiekt typu [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Wymagania

[STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) lub nowszej

**Nagłówek:** \<string_view >

**Namespace:** standardowe

## <a name="at"></a>  basic_string_view::AT

Zwraca const_reference znak pod określonym indeksem oparty na 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Indeks elementu, który ma być przywoływane.

### <a name="return-value"></a>Wartość zwracana

Const_reference — znak na pozycji określonej przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a także następujące elementy są indeksowane po kolei, dodatnie liczby całkowite, tak aby string_view o długości *n* ma *n*th elementu indeksowane przez numer *n -* 1. **w** zgłasza wyjątek dla nieprawidłowy indeksów, w odróżnieniu od [operator\[\]](#op_at). 

Ogólnie rzecz biorąc, zaleca się, że **na** sekwencji, takie jak `std::vector` i string_view nigdy nie powinna być używana. Nieprawidłowy indeks przekazany do sekwencji jest błąd logiczny, który powinien być wykryte i rozwiązane podczas tworzenia. Jeśli program nie jest absolutną pewność, że jej indeksów są prawidłowe, powinien je przetestować, nie wywołać at() i polegają na wyjątkach podczas obrony przed nieostrożnej programowania.

Zobacz [basic_string_view::operator\[ \] ](#op_at) Aby uzyskać więcej informacji.

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

## <a name="back"></a>  basic_string_view::back

Const_reference — zwraca ostatni element.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference — do ostatniego elementu w string_view.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusta.

Należy pamiętać, że po zmodyfikowaniu string_view, na przykład przez wywołanie metody `remove_suffix`, a następnie element zwrócona przez tę funkcję nie jest już po ostatnim elemencie w danych bazowych.

### <a name="example"></a>Przykład

String_view, który jest konstruowany przy użyciu literału ciągu języka C nie obejmuje kończącą wartość null, dlatego w poniższym przykładzie `back` zwraca "p", a nie '\0'.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Osadzone wartości są traktowane jako jakikolwiek inny znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

Tworzy string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Wskaźnik do wartości znakowych.

*len*<br/>
Liczba znaków, aby uwzględnić w widoku.

## <a name="remarks"></a>Uwagi

Konstruktorów z parametrem wykresu * przyjęto założenie, że dane wejściowe są zakończony znakiem null, ale zakończenia o wartości null nie jest uwzględniony w string_view.

Można także skonstruować string_view z literałem. Zobacz [operator "" sv](string-view-operators.md#op_sv).

## <a name="begin"></a>  basic_string_view::BEGIN

Taki sam jak [cbegin —](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana
Zwraca const_iterator adresujący pierwszy element.

## <a name="cbegin"></a>  basic_string_view::cbegin

Zwraca const_iterator, odnoszący się do pierwszego elementu w zakresie.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

## <a name="cend"></a>  basic_string_view::cend

Zwraca const_iterator, odnoszący się do lokalizacji tuż za ostatnim elementem w zakresie.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iteratora dostępu swobodnego, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

## <a name="compare"></a> basic_string_view::COMPARE

Wykonuje porównanie z uwzględnieniem wielkości liter z określoną string_view (lub typem możliwa do przekonwertowania ciągu) do ustalenia, czy dwa obiekty są równe, lub jeśli jest leksykograficznie krótszy niż drugi. [ \<String_view > operatorów](string-view-operators.md) użyć tej funkcji elementu członkowskiego do wykonania porównania.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parametry

*strv*<br/>
String_view, który ma być porównywana z tym string_view.

*punktu sprzedaży*<br/>
Indeks tego string_view, od której rozpoczyna się porównania.

*num*<br/>
Maksymalna liczba znaków z tym string_view mają być porównane.

*num2*<br/>
Maksymalna liczba znaków z *strv* mają być porównane.

*offset*<br/>
Indeks *strv* od którego rozpoczyna się porównania.

*ptr*<br/>
Ciąg języka C do porównania z tym string_view.

### <a name="return-value"></a>Wartość zwracana

Wartość ujemną, jeśli jest to string_view mniej niż *strv* lub *ptr*; zero, jeżeli sekwencje znaków dwa są równe; lub wartość dodatnią, jeśli ta string_view jest większa niż *strv*lub *ptr*.

### <a name="remarks"></a>Uwagi

`compare` Funkcje Członkowskie wykonania porównania uwzględniającego wielkość liter w całości lub części każdego sekwencji znaków. 

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

## <a name="copy"></a>  basic_string_view::Copy

Kopiuje co najwyżej określoną liczbę znaków z indeksowanej pozycji w string_view źródłowej do docelowej tablicy znaków. Firma Microsoft zaleca, aby używać funkcji bezpiecznego [basic_string_view::_Copy_s](#_copy_s) zamiast tego.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Tablica docelowa znak, do którego mają zostać skopiowane elementy.

*Liczba*<br/>
Liczba znaków do skopiowania, co najwyżej z string_view źródła.

*offset*<br/>
Pozycja początku string_view źródło, z którego mają zostać wprowadzone kopii.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

Zabezpieczanie funkcji kopiowania CRT ma być używany zamiast [kopiowania](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Tablica docelowa znak, do którego mają zostać skopiowane elementy.

*dest_size*<br/>
Rozmiar *dest*.

_ *Liczba* liczba znaków do skopiowania, co najwyżej z ciągu źródłowego.

*_Off*<br/>
Pozycję początkową w ciągu źródłowym, z którego mają zostać wprowadzone kopii.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

 Aby uzyskać więcej informacji, zobacz [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>  basic_string_view::crbegin

Zwraca const_reverse_iterator, odnoszący się do pierwszego elementu w odwróconym string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Const_reverse_iterator — odnoszący się do pierwszego elementu w odwróconym string_view. 

## <a name="crend"></a>  basic_string_view::crend

Taki sam jak [rend —](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_reverse_iterator, odnoszący się do jednego poza końcem string_view odwróconej.

## <a name="data"></a>  basic_string_view::Data

Zwraca surowy wskaźnik nie będący właścicielem const sekwencję znaków, obiektu, który został użyty do utworzenia string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do const do pierwszego elementu w sekwencji znaków.

### <a name="remarks"></a>Uwagi

Wskaźnik nie można zmodyfikować znaków.

Sekwencja znaków string_view jest zawsze zakończony znakiem null. Typ zwracany dla `data` nie jest prawidłowym ciągiem C, ponieważ pobiera dołączany nie znaku null. Znak null '\0' nie ma specjalnego znaczenia w obiekcie typu string_view i może być częścią obiektu string_view, podobnie jak jakikolwiek inny znak.

## <a name="empty"></a>  basic_string_view::Empty

Sprawdza, czy string_view zawiera znaki, czy nie.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt string_view nie zawiera żadnych znaków; **false** ma co najmniej jeden znak.

### <a name="remarks"></a>Uwagi

Funkcja członkowska jest odpowiednikiem [rozmiar](#size)() == 0.

## <a name="end"></a>  basic_string_view::end

Zwraca const_iterator dostępu losowego, który wskazuje na jednym elementem.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca const_iterator dostępu losowego, który wskazuje na jednym elementem.

### <a name="remarks"></a>Uwagi

`end` Służy do sprawdzenia, czy const_iterator osiągnął koniec swojej string_view. Wartość zwrócona przez obiekt `end` nie należy usuwać odwołania.

## <a name="find"></a>  basic_string_view::Find

Wyszukuje string_view w kierunku do przodu dla pierwszego wystąpienia znaku lub podciągu, który odpowiada określonej sekwencji znaków.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym ma się rozpocząć wyszukiwanie.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków w *ptr*, licząc do przodu, od pierwszego znaku.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego wystąpienia znaku podciągu wyszukiwane Jeśli operacja się powiedzie; w przeciwnym razie `npos`.

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

Wyszukuje pierwszy znak, który nie jest elementem określonego string_view lub przekonwertowania ciągu obiektu.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym ma się rozpocząć wyszukiwanie.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków, licząc do przodu, od pierwszego wystąpienia znaku w ciągu języka C, dla którego funkcja członkowska jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego wystąpienia znaku podciągu wyszukiwane Jeśli operacja się powiedzie; w przeciwnym razie `npos`.

## <a name="find_first_of"></a>  basic_string_view::find_first_of

Wyszukuje pierwszy znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym ma się rozpocząć wyszukiwanie.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków, licząc do przodu, od pierwszego wystąpienia znaku w ciągu języka C, dla którego funkcja członkowska jest do wyszukiwania.

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego wystąpienia znaku podciągu wyszukiwane Jeśli operacja się powiedzie; w przeciwnym razie `npos`.

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

Wyszukuje ostatni znak, który nie jest żadnym elementem określonego string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym Zakończ wyszukiwania.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków, licząc w przód od pierwszego wystąpienia znaku w *ptr*.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego wystąpienia znaku podciągu wyszukiwane Jeśli operacja się powiedzie; w przeciwnym razie `string_view::npos`.

## <a name="find_last_of"></a>  basic_string_view::find_last_of

Wyszukuje ostatni znak, który pasuje do dowolnego elementu określonego string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym Zakończ wyszukiwania.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków, licząc do przodu, od pierwszego wystąpienia znaku w ciągu języka C, dla którego funkcja członkowska jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego znaku podciąg wyszukiwane Jeśli operacja się powiedzie; w przeciwnym razie `npos`.

## <a name="front"></a>  basic_string_view::front

Const_reference — zwraca pierwszy element.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Const_reference — do pierwszego elementu.

### <a name="remarks"></a>Uwagi

Zgłasza wyjątek, jeśli string_view jest pusta.

## <a name="length"></a> basic_string_view::length

Zwraca aktualną liczbę elementów.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego jest taka sama jak [rozmiar](#size).

## <a name="max_size"></a>  basic_string_view::max_size

Zwraca maksymalną liczbę znaków, które mogą zawierać string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna liczba znaków, które mogą zawierać string_view.

### <a name="remarks"></a>Uwagi

Wyjątek typu [length_error](../standard-library/length-error-class.md) jest zgłaszany, gdy operacja daje string_view o długości większej niż `max_size()`.

## <a name="op_eq"></a>  basic_string_view::operator =

Przypisuje string_view lub przekonwertować obiekt ciągu do innego string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Przykład

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  [] basic_string_view::operator

Udostępnia const_reference do znaku o określonym indeksie.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Indeks elementu, który ma być przywoływane.

### <a name="return-value"></a>Wartość zwracana

Const_reference — znak na pozycji określonej przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ma indeks zero, a także następujące elementy są indeksowane po kolei, dodatnie liczby całkowite, tak aby string_view o długości *n* ma *n*th elementu indeksowane przez numer *n* - 1.

`operator[]` jest szybsza niż funkcja elementu członkowskiego [na](#at) zapewniające dostęp do odczytu do elementów string_view.

`operator[]` nie sprawdza, czy wskaźnik przekazywany jako argument jest nieprawidłowy. Nieprawidłowy indeks przekazany do `operator[]` powoduje zachowanie niezdefiniowane.

Odwołanie zwrócone może unieważniony, jeśli ciąg danych jest zmodyfikowany lub usunięty przez obiekt-właściciel.

Podczas kompilowania za pomocą [ \_ITERATORA\_debugowania\_poziom](../standard-library/iterator-debug-level.md) równa 1 lub 2, wystąpi błąd czasu wykonywania przy próbie uzyskania dostępu do elementu poza granicami string_view. Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>  basic_string_view::rbegin

Zwraca const iterator do pierwszego elementu w odwróconym string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca iterator dostępu losowego do pierwszego elementu w odwróconym string_view, adresowania, jaki byłyby po ostatnim elemencie w odpowiedniej string_view nieodwróconej.

### <a name="remarks"></a>Uwagi

`rbegin` jest używana z odwróconej string_view podobnie jak [rozpocząć](#begin) jest używana z string_view. `rbegin` może służyć do tyłu zainicjować iteracji.

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

Przesuwa wskaźnik myszy do przodu przez określoną liczbę elementów.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia danych bazowych, bez zmian. Przesuwa do przodu wskaźnik string_view n elementów i ustawia prywatna `size` element członkowski danych do rozmiaru - n.

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

Zmniejsza rozmiar widoku przez określoną liczbę elementów, poczynając od tyłu.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Uwagi

Pozostawia danych bazowych i wskaźnika do niego bez zmian. Ustawia prywatna `size` element członkowski danych do rozmiaru - n.

## <a name="rend"></a>  basic_string_view::rend

Zwraca iterator const, który wskazuje na po ostatnim elemencie w odwróconej string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Stała odwrotnego iteratora dostępu swobodnego, który wskazuje na po ostatnim elemencie w odwróconej string_view.

### <a name="remarks"></a>Uwagi

`rend` jest używana z odwróconej string_view podobnie jak [zakończenia](#end) jest używana z string_view. `rend` może służyć do sprawdzenia, czy wsteczny iterator osiągnął koniec swojej string_view. Wartość zwrócona przez obiekt `rend` nie należy usuwać odwołania.

## <a name="rfind"></a>  basic_string_view::rfind

Wyszukuje string_view w odwrotnej kolejności dla podciągu, który odpowiada określonej sekwencji znaków.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal*<br/>
Wartość znaku, dla którego funkcja członkowska jest do wyszukiwania.

*offset*<br/>
Indeks, w którym ma się rozpocząć wyszukiwanie.

*ptr*<br/>
Ciąg C, dla którego funkcja członkowska jest do wyszukiwania.

*Liczba*<br/>
Liczba znaków, licząc do przodu, od pierwszego wystąpienia znaku w ciągu języka C, dla którego funkcja członkowska jest do wyszukiwania.

*str*<br/>
String_view, dla którego funkcja członkowska jest do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Indeks pierwszego znaku podciąg, jeśli operacja się powiedzie; w przeciwnym razie `npos`.

## <a name="size"></a>  basic_string_view::size

Zwraca liczbę elementów w string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Długość string_view.

### <a name="remarks"></a>Uwagi

String_view można zmodyfikować jego długość, na przykład `remove_prefix` i `remove_suffix`. Ponieważ nie modyfikuje danych bazowych ciągu, rozmiar string_view nie jest koniecznie rozmiar danych bazowych.

## <a name="substr"></a>  basic_string_view::substr

Zwraca string_view, który reprezentuje (maksymalnie) określoną liczbę znaków od określonej pozycji.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*offset*<br/>
Indeks lokalizacji elementu w miejscu, z którego wykonano kopię, przy użyciu wartości domyślnej 0.

*Liczba*<br/>
Liczba znaków, które mają zostać objęte podciąg, jeśli są obecne.

### <a name="return-value"></a>Wartość zwracana

Obiekt string_view, który reprezentuje określony podrzędny sekwencję elementów.

## <a name="swap"></a>  basic_string_view::swap

Zamienia dwa string_views, innymi słowy wskaźników do danych bazowych ciąg i wartości rozmiaru.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*sv*<br/>
String_view źródła, w których wartości wskaźnika i rozmiaru są wymieniane z tymi, które string_view docelowego.

## <a name="see-also"></a>Zobacz także

[\<string_view >](../standard-library/string-view.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
