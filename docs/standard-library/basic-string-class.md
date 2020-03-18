---
title: basic_string — Klasa
ms.date: 11/12/2019
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::swap
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 08620e0ae6b54b106daba8e0b0a392ceb1a6577d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422032"
---
# <a name="basic_string-class"></a>basic_string — Klasa

Sekwencje kontrolowane przez obiekt typu `basic_string` są klasą ciągu standardowego C++ i są zwykle określane jako ciągi, ale nie należy ich mylić z ciągami stylu języka C zakończonymi zerem używanymi w całej bibliotece C++ standardowej. Standardowy C++ ciąg jest kontenerem, który umożliwia korzystanie z ciągów jako zwykłych typów, takich jak operacje porównania i łączenia, Iteratory, C++ algorytmy standardowej biblioteki oraz kopiowanie i przypisywanie pamięci zarządzanej przy użyciu programu przydzielania klas. Jeśli zachodzi potrzeba przekonwertowania standardowego C++ ciągu na ciąg w stylu C zakończony wartością null, użyj elementu członkowskiego [basic_string:: c_str](#c_str) .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>Parametry

\ *CharType*
Typ danych pojedynczego znaku, który ma być przechowywany w ciągu. Biblioteka C++ standardowa zawiera specjalizacje tego szablonu klasy, z [ciągiem](../standard-library/string-typedefs.md#string) definicji typów dla elementów typu **char**, [wstring](../standard-library/string-typedefs.md#wstring), dla **wchar_t**, [u16string](../standard-library/string-typedefs.md#u16string) dla `char16_t`i [u32string](../standard-library/string-typedefs.md#u32string) dla `char32_t`.

*Cechy*\
Różne ważne właściwości elementów `CharType` w specjalizacji basic_string są opisane przez `Traits`klasy. Wartość domyślna to `char_traits`< `CharType`>.

\ *alokatora*
Typ reprezentujący przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji ciągu i cofania przydziału pamięci. Wartość domyślna to **alokator**< `CharType`>.

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[basic_string](#basic_string)|Konstruuje ciąg, który jest pusty lub inicjowany przez określone znaki lub jest kopią całości lub części innego obiektu ciągu lub ciągu C.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę `allocator` dla obiektu String.|
|[const_iterator](#const_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskać dostęp i odczytać element **const** w ciągu.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** w ciągu.|
|[const_reference](#const_reference)|Typ, który dostarcza odwołanie do elementu **const** przechowywanego w ciągu do odczytu i wykonywania operacji **const** .|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element **const** w ciągu.|
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego ciągu.|
|[Iterator](#iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować dowolny element w ciągu.|
|[npos](#npos)|Wartość całkowita bez znaku została zainicjowana do-1, która wskazuje "nie znaleziono" lub "wszystkie pozostałe znaki", gdy funkcja wyszukiwania zakończy się niepowodzeniem.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu znaku w ciągu lub tablicy znaków.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu przechowywanego w ciągu.|
|[reverse_iterator](#reverse_iterator)|Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać lub zmodyfikować element w ciągu odwróconym.|
|[size_type](#size_type)|Niepodpisany typ całkowity dla liczby elementów w ciągu.|
|[traits_type](#traits_type)|Typ cech znaków elementów przechowywanych w ciągu.|
|[value_type](#value_type)|Typ, który reprezentuje typ znaków przechowywanych w ciągu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[łączono](#append)|Dodaje znaki na końcu ciągu.|
|[ponownie](#assign)|Przypisuje nowe wartości znakowe do zawartości ciągu.|
|[w](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w ciągu.|
|[Wstecz](#back)||
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu w ciągu.|
|[c_str](#c_str)|Konwertuje zawartość ciągu jako styl C, zakończony zerem, String.|
|[pojemności](#capacity)|Zwraca największą liczbę elementów, które mogą być przechowywane w ciągu bez zwiększania alokacji pamięci ciągu.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu w ciągu.|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie w ciągu.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy ciągu.|
|[porównaniu](#compare)|Porównuje ciąg z określonym ciągiem, aby określić, czy dwa ciągi są równe lub czy jeden z nich jest lexicographically mniejszy od drugiego.|
|[kopiowane](#copy)|Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w ciągu źródłowym do docelowej tablicy znaków. Przestarzałe. Zamiast tego użyj [basic_string:: _Copy_s](#copy_s) .|
|[crbegin —](#crbegin)|Zwraca iterator const, który odnosi się do pierwszego elementu w ciągu odwróconym.|
|[crend](#crend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w ciągu odwróconym.|
|[_Copy_s](#copy_s)|Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w ciągu źródłowym do docelowej tablicy znaków.|
|[Data](#data)|Konwertuje zawartość ciągu na tablicę znaków.|
|[ciągiem](#empty)|Testuje, czy ciąg zawiera znaki.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w ciągu.|
|[Wyłączanie](#erase)|Usuwa element lub zakres elementów w ciągu z określonego położenia.|
|[find](#find)|Wyszukuje ciąg w kierunku do przodu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[find_first_not_of](#find_first_not_of)|Wyszukuje w ciągu pierwszy znak, który nie jest żadnym elementem określonego ciągu.|
|[find_first_of](#find_first_of)|Wyszukuje w ciągu pierwszy znak, który pasuje do dowolnego elementu określonego ciągu.|
|[find_last_not_of](#find_last_not_of)|Wyszukuje w ciągu ostatni znak, który nie jest żadnym elementem określonego ciągu.|
|[find_last_of](#find_last_of)|Wyszukuje w ciągu ostatni znak, który jest elementem określonego ciągu.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu w ciągu.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu `allocator` użytego do skonstruowania ciągu.|
|[wstawienia](#insert)|Wstawia element lub liczbę elementów lub zakres elementów do ciągu w określonej pozycji.|
|[Długość](#length)|Zwraca bieżącą liczbę elementów w ciągu.|
|[max_size](#max_size)|Zwraca maksymalną liczbę znaków, jaką może zawierać ciąg.|
|[pop_back](#pop_back)|Wymazuje ostatni element ciągu.|
|[push_back](#push_back)|Dodaje element na końcu ciągu.|
|[rbegin](#rbegin)|Zwraca iterator do pierwszego elementu w ciągu odwróconym.|
|[rend](#rend)|Zwraca iterator, który wskazuje tuż poza ostatnim elementem w ciągu odwróconym.|
|[stępować](#replace)|Zamienia elementy w ciągu w określonej pozycji z określonymi znakami lub znakami skopiowanymi z innych zakresów lub ciągów lub ciągów języka C.|
|[zarezerwować](#reserve)|Ustawia pojemność ciągu na liczbę, która jest co najmniej równa podanej liczbie.|
|[Zmień rozmiar](#resize)|Określa nowy rozmiar ciągu, dołączając lub wymazywając elementy zgodnie z wymaganiami.|
|[rfind](#rfind)|Wyszukuje ciąg w kierunku do tyłu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.|
|[shrink_to_fit](#shrink_to_fit)|Odrzuca nadmiarową pojemność ciągu.|
|[zmienia](#size)|Zwraca bieżącą liczbę elementów w ciągu.|
|[substr —](#substr)|Kopiuje podciąg z co najwyżej określoną liczbę znaków z ciągu rozpoczynającego się od określonej pozycji.|
|[wymiany](#swap)|Wymiana zawartości dwóch ciągów.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator + =](#op_add_eq)|Dołącza znaki do ciągu.|
|[operator =](#op_eq)|Przypisuje nowe wartości znakowe do zawartości ciągu.|
|[zakład&#91;&#93;](#op_at)|Zawiera odwołanie do znaku o określonym indeksie w ciągu.|

## <a name="remarks"></a>Uwagi

Jeśli zostanie wyświetlona prośba o wygenerowanie sekwencji dłuższej niż [max_size](#max_size) elementów, funkcja zgłasza błąd długości przez wygenerowanie obiektu typu [length_error](../standard-library/length-error-class.md).

Odwołania, wskaźniki i Iteratory, które wyznaczają elementy kontrolowanej sekwencji, mogą stać się nieprawidłowe po dowolnych wywołaniach funkcji, które zmieniają kontrolowane sekwencje lub po pierwszym wywołaniu **niestałej** funkcji składowej.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ciąg >

**Przestrzeń nazw:** std

## <a name="allocator_type"></a>basic_string:: allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu ciągu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Allocator`.

### <a name="example"></a>Przykład

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="append"></a>basic_string:: Append

Dodaje znaki na końcu ciągu.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ciąg C, który ma zostać dołączony.

*str*\
Ciąg, którego znaki mają być dołączane.

\ *przesunięcia*
Indeks części ciągu źródłowego dostarczającego znaki do dołączenia.

*liczba*\
Liczba znaków, które mają być dołączane, w ciągu źródłowym.

*char_value*\
Wartość znaku, która ma zostać dołączona.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie, który ma zostać dołączony.

*ostatni*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pozycji jednego z nich poza ostatnim elementem w zakresie, który ma zostać dołączony.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu ciągu, który jest dołączany do znaków przesłanych przez funkcję członkowską.

### <a name="remarks"></a>Uwagi

Znaki mogą być dołączane do ciągu przy użyciu [operatora + =](#op_add_eq) lub funkcji składowych `append` lub [push_back](#push_back). `operator+=` dołącza wartości jednoargumentowe, podczas gdy wieloargumentowy `append` funkcja członkowska umożliwia określenie określonej części ciągu do dodania.

### <a name="example"></a>Przykład

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="assign"></a>basic_string:: Assign

Przypisuje nowe wartości znakowe do zawartości ciągu.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik do znaków znaku C, który ma zostać przypisany do ciągu docelowego.

*liczba*\
Liczba znaków, które mają być przypisane, z ciągu źródłowego.

*str*\
Ciąg źródłowy, którego znaki mają być przypisane do ciągu docelowego.

*char_value*\
Wartość znaku, która ma zostać przypisana.

*pierwszy*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pierwszego znaku w zakresie ciągu źródłowego, który ma zostać przypisany do zakresu docelowego.

*ostatni*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do jednego z nich poza ostatnim znakiem z zakresu ciągu źródłowego, który ma zostać przypisany do zakresu docelowego.

*wyłączone*\
Pozycja, w której mają zostać przypisane nowe znaki.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu String, do którego są przypisywane nowe znaki przez funkcję członkowską.

### <a name="remarks"></a>Uwagi

Do ciągów można przypisać nowe wartości znakowe. Nowa wartość może być ciągiem i ciągiem C lub pojedynczym znakiem. [Operatora =](#op_eq) można użyć, jeśli nowa wartość może być opisana przez pojedynczy parametr; w przeciwnym razie funkcja członkowska `assign`, która ma wiele parametrów, może służyć do określenia, która część ciągu ma zostać przypisana do ciągu docelowego.

### <a name="example"></a>Przykład

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="at"></a>basic_string:: at

Zawiera odwołanie do znaku o określonym indeksie w ciągu.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>Parametry

\ *przesunięcia*
Indeks pozycji elementu, do którego ma zostać utworzone odwołanie.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do znaku ciągu w pozycji określonej przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ciągu ma indeks zero, a następujące elementy są indeksowane po kolei przez dodatnie liczby całkowite, tak aby ciąg o długości *n* miał element *n*, który jest indeksowany przez liczbę *n-* 1.

[Operator&#91; ](#op_at) elementu członkowskiego jest szybszy niż funkcja członkowska `at` do zapewniania dostępu do odczytu i zapisu do elementów ciągu.

`operator[]` elementu członkowskiego nie sprawdza, czy indeks przeszedł jako parametr jest prawidłowy, ale funkcja członkowska `at` wykonuje i dlatego powinna zostać użyta, jeśli nie określono ważności. Nieprawidłowy indeks, który jest indeksem o wartości równej zero lub większym lub równym rozmiarowi ciągu, został przesłany do funkcji składowej `at` zgłasza wyjątek [klasy out_of_range](../standard-library/out-of-range-class.md) . Nieprawidłowy indeks przeszedł do `operator[]` skutkuje niezdefiniowanym zachowaniem, ale indeks równy długości ciągu jest prawidłowym indeksem dla stałych ciągów, a operator zwraca znak null, gdy przeszedł ten indeks.

Zwrócone odwołanie może być unieważnione przez ponowne alokacje ciągu lub modyfikacje ciągów **niestałych** .

### <a name="example"></a>Przykład

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="back"></a>basic_string:: Back

Zwraca odwołanie do ostatniego elementu w ciągu.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do ostatniego elementu ciągu, który nie może być pusty.

### <a name="remarks"></a>Uwagi

## <a name="basic_string"></a>basic_string:: basic_string

Konstruuje ciąg, który jest pusty, zainicjowany przez określone znaki lub jest kopią całości lub części innego obiektu String lub ciągu C (zakończony zerem).

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ciąg języka C, którego znaki mają być używane do inicjowania konstruowanych `string`. Ta wartość nie może być pustym wskaźnikiem.

*alloc_type*\
Klasa alokatora magazynu dla obiektu ciągu, który jest konstruowany.

*liczba*\
Liczba znaków, które mają zostać zainicjowane.

*prawa*\
Ciąg, w którym ma zostać zainicjowany tworzony ciąg.

*right_offset*\
Indeks znaku w ciągu, który jest pierwszym używany do inicjowania wartości znakowych dla konstruowanego ciągu.

*char_value*\
Wartość znaku do skopiowania do ciągu, który jest tworzony.

*pierwszy*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pierwszego elementu w zakresie źródłowym, który ma zostać wstawiony.

*ostatni*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pozycji jednego z nich poza ostatnim elementem w zakresie źródłowym, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu String, który jest konstruowany przez konstruktory.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują [basic_string:: allocator_type](#allocator_type) i inicjują kontrolowaną sekwencję. Obiekt alokatora jest argumentem `al`, jeśli jest obecny. Dla konstruktora kopiującego jest `right.`[basic_string:: get_allocator](#get_allocator)`()`. W przeciwnym razie Alokator jest `Alloc()`.

Kontrolowana sekwencja jest inicjowana do kopii sekwencji operandu określonej przez pozostałe operandy. Konstruktor bez sekwencji operandu określa pustą sterowaną sekwencję. Jeśli `InputIterator` jest typem liczb całkowitych w konstruktorze szablonów, sekwencja operandu `first,  last` zachowuje się tak samo jak `(size_type) first, (value_type) last`.

### <a name="example"></a>Przykład

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="begin"></a>basic_string:: BEGIN

Zwraca iterator odnoszący się do pierwszego elementu w ciągu.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator dostępu swobodnego, który odnosi się do pierwszego elementu sekwencji lub tuż poza końcem pustej sekwencji.

### <a name="example"></a>Przykład

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="c_str"></a>basic_string:: c_str

Konwertuje zawartość ciągu jako styl języka C, ciąg zakończony znakiem null.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do wersji stylu języka C wywołującego ciąg.  Wartość wskaźnika jest nieprawidłowa po wywołaniu funkcji innej niż stała, w tym destruktora, w klasie basic_string w obiekcie.

### <a name="remarks"></a>Uwagi

Obiekty typu String należące do szablonu klasy basic_string\<char > nie muszą kończyć się wartością null. Znak null "\ 0" jest używany jako znak specjalny w ciągu C do oznaczania końca ciągu, ale nie ma specjalnego znaczenia w obiekcie typu String i może być częścią ciągu tak samo jak każdy inny znak. Istnieje Automatyczna konwersja z **stałej char** <strong>\*</strong> na ciągi, ale Klasa String nie zapewnia automatycznych konwersji z ciągów w stylu C na obiekty typu **basic_string\<char >** .

Nie należy modyfikować zwracanego ciągu w stylu C, ponieważ może to spowodować sprawdzenie poprawności wskaźnika do ciągu lub usunięcie, ponieważ ciąg ma ograniczony okres istnienia i jest własnością ciągu klasy.

### <a name="example"></a>Przykład

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="capacity"></a>basic_string:: pojemność

Zwraca największą liczbę elementów, które mogą być przechowywane w ciągu bez zwiększania alokacji pamięci ciągu.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Wartość zwrócona

Rozmiar magazynu aktualnie przydzielony w pamięci w celu przechowania ciągu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca magazyn aktualnie przydzielony do przechowania kontrolowanej sekwencji, co najmniej tak duże jak [rozmiar](#size).

### <a name="example"></a>Przykład

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="cbegin"></a>basic_string:: cbegin

Zwraca iterator **const** , który dotyczy pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator **const** dostępu swobodnego, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin`nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `begin()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>basic_string:: cend

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator **stałej** dostępu swobodnego, który wskazuje tuż poza końcem zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `end()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie należy wywoływać wartości zwracanej przez `cend`.

## <a name="clear"></a>basic_string:: Clear

Usuwa wszystkie elementy ciągu.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Ciąg, w którym wywoływana jest funkcja członkowska, będzie pusty.

### <a name="example"></a>Przykład

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="compare"></a>basic_string:: Compare

Wykonuje porównanie z uwzględnieniem wielkości liter z określonym ciągiem, aby określić, czy dwa ciągi są równe, czy też jest lexicographically mniejsze niż inne.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>Parametry

*str*\
Ciąg, który ma zostać porównany z ciągiem operandu.

*position_1*\
Indeks ciągu operandu, w którym rozpoczyna się porównywanie.

*number_1*\
Maksymalna liczba znaków z ciągu operandu do porównania.

*number_2*\
Maksymalna liczba znaków z ciągu parametru do porównania.

\ *przesunięcia*
Indeks ciągu parametru, w którym rozpoczyna się porównywanie.

*liczba*\
Maksymalna liczba znaków z ciągu parametru do porównania.

\ *PTR*
Ciąg języka C, który będzie porównywany z ciągiem operandu.

### <a name="return-value"></a>Wartość zwrócona

Wartość ujemna, jeśli ciąg operandu jest krótszy niż ciąg parametru; zero, jeśli dwa ciągi są równe; lub wartość dodatnia, jeśli ciąg operandu jest większy niż ciąg parametru.

### <a name="remarks"></a>Uwagi

Funkcje składowe `compare` porównują wszystkie parametry i argumenty operandu, w zależności od używanej wartości.

W przypadku porównania jest uwzględniana wielkość liter.

### <a name="example"></a>Przykład

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="const_iterator"></a>basic_string:: const_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskać dostęp i odczytać element **const** w ciągu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

Typu `const_iterator` nie można użyć do zmodyfikowania wartości znaku i służy do iteracji ciągu w kierunku do przodu.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `const_iterator`.

## <a name="const_pointer"></a>basic_string:: const_pointer

Typ, który dostarcza wskaźnik do elementu **const** w ciągu.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `allocator_type::const_pointer`.

W przypadku typu `string`jest to równoznaczne z `char*`.

Wskaźniki, które są zadeklarowane jako const, muszą być inicjowane, gdy są zadeklarowane. Wskaźniki stałe zawsze wskazują tę samą lokalizację pamięci i mogą wskazywać na stałe lub niestałe dane.

### <a name="example"></a>Przykład

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="const_reference"></a>basic_string:: const_reference

Typ, który dostarcza odwołanie do elementu **const** przechowywanego w ciągu do odczytu i wykonywania operacji **const** .

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

Typu `const_reference` nie można użyć do zmodyfikowania wartości elementu.

Typ jest synonimem dla `allocator_type::const_reference`. W przypadku ciągów `type`jest równoważne `char&`const.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem, [Aby uzyskać przykład](#at) sposobu deklarowania i używania `const_reference`.

## <a name="const_reverse_iterator"></a>basic_string:: const_reverse_iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może odczytać dowolny element **const** w ciągu.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `const_reverse_iterator` nie może zmodyfikować wartości znaku i służy do iteracji ciągu w odwrotnej postaci.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `const_reverse_iterator`.

## <a name="copy"></a>basic_string:: Copy

Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w ciągu źródłowym do docelowej tablicy znaków.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne. Zamiast tego Rozważ użycie [basic_string:: _Copy_s](#copy_s) .

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Docelowa tablica znaków, do której mają zostać skopiowane elementy.

*Liczba* Maksymalna liczba znaków, które mają być skopiowane, z ciągu źródłowego.

\ *przesunięcia*
Pozycja początkowa w ciągu źródłowym, z którego mają zostać wykonane kopie.

### <a name="return-value"></a>Wartość zwrócona

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

### <a name="example"></a>Przykład

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="crbegin"></a>basic_string:: crbegin —

Zwraca iterator const, który odnosi się do pierwszego elementu w ciągu odwróconym.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odwrotny, który wskazuje tuż poza końcem ciągu. Pozycja określa początek ciągu odwrotnego.

## <a name="crend"></a>basic_string:: crend

Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie w ciągu odwróconym.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Wartość zwrócona

Iterator zwrotny const, który odnosi się do lokalizacji po ostatnim elemencie w odwróconym ciągu (lokalizacja, która poprzedza pierwszy element w ciągu nieodwróconym).

### <a name="remarks"></a>Uwagi

## <a name="copy_s"></a>basic_string:: _Copy_s

Kopiuje co najwyżej określoną liczbę znaków z pozycji indeksowanej w ciągu źródłowym do docelowej tablicy znaków.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

\ miejsca *docelowego*
Docelowa tablica znaków, do której mają zostać skopiowane elementy.

*dest_size*\
Rozmiar miejsca *docelowego*.

*Liczba* Maksymalna liczba znaków, które mają być skopiowane, z ciągu źródłowego.

\ *przesunięcia*
Pozycja początkowa w ciągu źródłowym, z którego mają zostać wykonane kopie.

### <a name="return-value"></a>Wartość zwrócona

Liczba znaków rzeczywiście skopiowanych.

### <a name="remarks"></a>Uwagi

Znak null nie jest dołączany na końcu kopii.

### <a name="example"></a>Przykład

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="data"></a>basic_string::d ATA

Konwertuje zawartość ciągu na tablicę znaków zakończonych znakiem null.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do pierwszego elementu tablicy zakończonych wartością null zawierający zawartość ciągu. W przypadku pustego ciągu wskaźnik wskazuje na pojedynczy znak o wartości null równy `value_type()`.

### <a name="remarks"></a>Uwagi

Wskaźnik zwrócony przez `data` punkty w prawidłowym zakresie `[data(), data() + size()]`. Każdy element w zakresie odpowiada bieżącym danym w ciągu. Oznacza to, dla każdego prawidłowego *przesunięcia w* zakresie, `data() + n == addressof(operator[](n))`.

Jeśli zmodyfikujesz zawartość ciągu zwracanego przez Przeciążenie **const** `data`, zachowanie jest niezdefiniowane. Możesz również uzyskać niezdefiniowane zachowanie, jeśli znak null terminalu zostanie zmieniony na inną wartość. Zwrócony wskaźnik może być unieważniony, jeśli odwołanie niestałe do ciągu zostanie przesłane do standardowej funkcji biblioteki. Może być również unieważniony przez wywołanie funkcji składowej innej niż stała. Wywołania elementów członkowskich `at`, `back`, `begin`, `end`, `front`, `rbegin`, `rend`i `operator[]` nie weryfikują wskaźnika. 

W starszych językach C++ 11 `data` nie zagwarantujeć, że zwrócony ciąg był zakończony wartością null. Od C++ 11 `data` i `c_str` zwracają ciąg zakończony znakiem null i są efektywnie takie same.

Przeciążenie inne niż const jest nowe w języku C++ 17. Aby go użyć, należy określić **/std: c++ 17** lub **/std: c + + Najnowsza** opcja kompilatora.

### <a name="example"></a>Przykład

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="difference_type"></a>basic_string::d ifference_type

Typ, który zawiera różnicę między dwoma iteratorami odwołującymi się do elementów w obrębie tego samego ciągu.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

Typ Liczba całkowita ze znakiem opisuje obiekt, który może reprezentować różnicę między adresami wszystkich dwóch elementów w kontrolowanej sekwencji.

W przypadku typu `string`jest to równoznaczne z `ptrdiff_t`.

### <a name="example"></a>Przykład

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="empty"></a>basic_string:: Empty

Testuje, czy ciąg zawiera znaki, czy nie.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obiekt String nie zawiera żadnych znaków; **wartość false** , jeśli ma co najmniej jeden znak.

### <a name="remarks"></a>Uwagi

Funkcja członkowska jest równoważna z [rozmiarem](#size) = = 0.

### <a name="example"></a>Przykład

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="end"></a>basic_string:: end

Zwraca iterator, który odnosi się do lokalizacji po ostatnim elemencie w ciągu.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca iterator dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w ciągu.

### <a name="remarks"></a>Uwagi

`end` jest często używany do testowania, czy iterator osiągnął koniec ciągu. Nie należy wywoływać wartości zwracanej przez `end`.

Jeśli wartość zwracana `end` jest przypisana do `const_iterator`, nie można zmodyfikować obiektu ciągu. Jeśli wartość zwracana `end` jest przypisana do `iterator`, można zmodyfikować obiekt ciągu.

### <a name="example"></a>Przykład

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="erase"></a>basic_string:: Erase

Usuwa element lub zakres elementów w ciągu z określonego położenia.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Iterator odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać wymazany.

*ostatni*\
Iterator odnoszący się do położenia jednej poza ostatnim elementem w zakresie, który ma zostać wymazany.

\ *ITER*
Iterator odnoszący się do pozycji elementu w ciągu, który ma zostać wymazany.

\ *przesunięcia*
Indeks pierwszego znaku w ciągu, który ma zostać usunięty.

*liczba*\
Liczba elementów, które zostaną usunięte, jeśli w zakresie ciągu rozpoczyna się od *przesunięcia*.

### <a name="return-value"></a>Wartość zwrócona

Dla pierwszych dwóch funkcji Członkowskich iterator odnoszący się do pierwszego znaku po ostatnim znaku usunięty przez funkcję członkowską. Dla trzeciej funkcji członkowskiej odwołanie do obiektu String, z którego elementy zostały wymazane.

### <a name="remarks"></a>Uwagi

Trzecia funkcja członkowska zwraca **\*tym**.

### <a name="example"></a>Przykład

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="find"></a>basic_string:: find

Wyszukuje ciąg w kierunku do przodu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać rozpoczęte wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'perfect' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="find_first_not_of"></a>basic_string:: find_first_not_of

Wyszukuje w ciągu pierwszy znak, który nie jest elementem określonego ciągu.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać rozpoczęte wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="find_first_of"></a>basic_string:: find_first_of

Wyszukuje w ciągu pierwszy znak, który pasuje do dowolnego elementu określonego ciągu.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać rozpoczęte wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="find_last_not_of"></a>basic_string:: find_last_not_of

Wyszukuje w ciągu ostatni znak, który nie jest żadnym elementem określonego ciągu.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać zakończone wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks pierwszego znaku podciągu, który jest przeszukiwany po pomyślnym; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="find_last_of"></a>basic_string:: find_last_of

Wyszukuje w ciągu ostatni znak, który pasuje do dowolnego elementu określonego ciągu.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać zakończone wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks ostatniego znaku podciągu przeszukiwany po pomyślnym; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="front"></a>basic_string:: front

Zwraca odwołanie do pierwszego elementu w ciągu.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do pierwszego elementu ciągu, który nie może być pusty.

### <a name="remarks"></a>Uwagi

## <a name="get_allocator"></a>basic_string:: get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania ciągu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwrócona

Alokator używany przez ciąg.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt alokatora.

Przypisania klasy String określają sposób, w jaki Klasa zarządza magazynem. Domyślne przydzielenie z klasami kontenerów jest wystarczające dla większości potrzeb programistycznych. Pisanie i używanie własnej klasy alokatora jest zaawansowanym C++ tematem.

### <a name="example"></a>Przykład

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="insert"></a>basic_string:: INSERT

Wstawia element lub liczbę elementów lub zakres elementów do ciągu w określonej pozycji.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

\ *pozycji*
Indeks pozycji za punktem wstawiania nowych znaków.

\ *PTR*
Ciąg C, który ma zostać w całości lub częściowo wstawiony do ciągu.

*liczba*\
Liczba znaków do wstawienia.

*str*\
Ciąg, który ma zostać całkowicie lub częściowo wstawiony do ciągu docelowego.

\ *przesunięcia*
Indeks części ciągu źródłowego dostarczającego znaki do dołączenia.

*char_value*\
Wartość znaku elementów do wstawienia.

\ *ITER*
Iterator odnoszący się do pozycji, w której ma zostać wstawiony znak.

*pierwszy*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pierwszego elementu w zakresie źródłowym, który ma zostać wstawiony.

*ostatni*\
Iterator danych wejściowych, const_pointer lub const_iterator odnoszący się do pozycji jednego z nich poza ostatnim elementem w zakresie źródłowym, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu String, do którego są przypisywane nowe znaki przez funkcję członkowską lub, w przypadku poszczególnych wstawień znaków, iterator odnoszący się do pozycji wstawionego znaku lub brak, w zależności od konkretnego elementu członkowskiego funkcyjn.

### <a name="example"></a>Przykład

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="iterator"></a>basic_string:: iterator

Typ, który dostarcza Iterator dostępu swobodnego, który może uzyskać dostęp i odczytać element **const** w ciągu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

Typ `iterator` może służyć do modyfikacji wartości znaku i służy do iteracji ciągu w kierunku do przodu.

### <a name="example"></a>Przykład

Zapoznaj [się](#begin) z przykładem dotyczącym sposobu deklarowania i używania `iterator`.

## <a name="length"></a>basic_string:: length

Zwraca bieżącą liczbę elementów w ciągu.

```cpp
size_type length() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska jest taka sama jak [rozmiar](#size).

### <a name="example"></a>Przykład

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="max_size"></a>basic_string:: max_size

Zwraca maksymalną liczbę znaków, jaką może zawierać ciąg.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Maksymalna liczba znaków, jaką może zawierać ciąg.

### <a name="remarks"></a>Uwagi

Wyjątek typu [klasy length_error](../standard-library/length-error-class.md) jest zgłaszany, gdy operacja generuje ciąg o długości większej niż maksymalny rozmiar.

### <a name="example"></a>Przykład

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="npos"></a>basic_string:: nPos

Wartość całkowita bez znaku została zainicjowana do-1, która wskazuje "nie znaleziono" lub "wszystkie pozostałe znaki", gdy funkcja wyszukiwania zakończy się niepowodzeniem.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>Uwagi

Gdy wartość zwracana ma być sprawdzana dla wartości `npos`, może ona nie działać, chyba że zwracana wartość jest typu [size_type](#size_type) i nie jest równa **int** ani **unsigned**.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dotyczącym [wyszukiwania](#find) , aby zapoznać się z przykładem sposobu deklarowania i używania `npos`.

## <a name="op_add_eq"></a>basic_string:: operator + =

Dołącza znaki do ciągu.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*char_value*\
Znak, który ma zostać dołączony.

\ *PTR*
Znaki ciągu C do dołączenia.

*prawa*\
Znaki ciągu do dołączenia.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu ciągu, który jest dołączany do znaków przesłanych przez funkcję członkowską.

### <a name="remarks"></a>Uwagi

Znaki mogą być dołączane do ciągu przy użyciu `operator+=` lub funkcji składowych [dołączania](#append) lub [push_back](#push_back). `operator+=` dołącza wartości pojedynczego argumentu, podczas gdy funkcja dołączająca wiele argumentów umożliwia określenie określonej części ciągu do dodania.

### <a name="example"></a>Przykład

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="op_eq"></a>basic_string:: operator =

Przypisuje nowe wartości znakowe do zawartości ciągu.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, która ma zostać przypisana.

\ *PTR*
Wskaźnik do znaków znaku C, który ma zostać przypisany do ciągu docelowego.

*prawa*\
Ciąg źródłowy, którego znaki mają być przypisane do ciągu docelowego.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do obiektu String, do którego są przypisywane nowe znaki przez funkcję członkowską.

### <a name="remarks"></a>Uwagi

Ciągi mogą mieć przypisane nowe wartości znakowe. Nowa wartość może być ciągiem i ciągiem C lub pojedynczym znakiem. `operator=` można użyć, jeśli nowa wartość może być opisana przez jeden parametr. w przeciwnym razie funkcja członkowska, która ma wiele parametrów, może być użyta do [określenia, która](#assign)część ciągu ma zostać przypisana do ciągu docelowego.

### <a name="example"></a>Przykład

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="op_at"></a>basic_string:: operator []

Zawiera odwołanie do znaku o określonym indeksie w ciągu.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>Parametry

\ *przesunięcia*
Indeks pozycji elementu, do którego ma zostać utworzone odwołanie.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do znaku ciągu w pozycji określonej przez indeks parametru.

### <a name="remarks"></a>Uwagi

Pierwszy element ciągu ma indeks zero, a następujące elementy są indeksowane po kolei przez dodatnie liczby całkowite, tak aby ciąg o długości *n* miał element *n*, który jest indeksowany przez liczbę *n* -1.

`operator[]` jest szybsza niż funkcja członkowska [na](#at) potrzeby zapewniania dostępu do odczytu i zapisu do elementów ciągu.

`operator[]` nie sprawdza, czy indeks przeszedł jako parametr jest prawidłowy, ale funkcja członkowska `at` wykonuje i dlatego powinna być używana w tym okresie ważności nie jest określona. Nieprawidłowy indeks (indeks bez znaku, który jest mniejszy niż lub równy rozmiarowi ciągu) przesłany do funkcji składowej `at` zgłasza wyjątek [klasy out_of_range](../standard-library/out-of-range-class.md) . Nieprawidłowy indeks przeszedł do `operator[]` skutkuje niezdefiniowanym zachowaniem, ale indeks równy długości ciągu jest prawidłowym indeksem dla ciągów stałych, a operator zwraca znak null, gdy przeszedł ten indeks.

Zwrócone odwołanie może być unieważnione przez ponowne alokacje ciągu lub modyfikacje ciągów **niestałych** .

Podczas kompilowania z użyciem [\_iteratora\_\_debugowania](../standard-library/iterator-debug-level.md) ustawionym na 1 lub 2, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu poza granicami ciągu. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="pointer"></a>basic_string::p ointer

Typ, który dostarcza wskaźnik do elementu znaku w ciągu lub tablicy znaków.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `allocator_type::pointer`.

Dla typu `string`jest to odpowiednik<strong>\*</strong> **znaków** .

### <a name="example"></a>Przykład

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="pop_back"></a>basic_string::p op_back

Wymazuje ostatni element ciągu.

```cpp
void pop_back();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego skutecznie wywołuje `erase(size() - 1)`, aby wymazać ostatni element sekwencji, który nie może być pusty.

## <a name="push_back"></a>basic_string::p ush_back

Dodaje element na końcu ciągu.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>Parametry

*char_value*\
Znak, który ma zostać dodany na końcu ciągu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska skutecznie wywołuje funkcję [INSERT](#insert)( [End](#end), *char_value* ).

### <a name="example"></a>Przykład

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="rbegin"></a>basic_string:: rbegin

Zwraca iterator do pierwszego elementu w ciągu odwróconym.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca iterator dostępu swobodnego do pierwszego elementu w ciągu odwróconym, na którym znajduje się ostatni element w odpowiadającym mu ciągu nieodwróconym.

### <a name="remarks"></a>Uwagi

`rbegin` jest używany z odwróconym ciągiem, tak jak [początek](#begin) jest używany z ciągiem.

Jeśli wartość zwracana `rbegin` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu ciągu. Jeśli wartość zwracana `rbegin` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt ciągu.

`rbegin` można użyć do zainicjowania iteracji za pomocą ciągu z poprzednimi wersjami.

### <a name="example"></a>Przykład

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="reference"></a>basic_string:: Reference

Typ, który zawiera odwołanie do elementu przechowywanego w ciągu.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>Uwagi

Typ `reference` może służyć do modyfikowania wartości elementu.

Typ jest synonimem dla `allocator_type::reference`.

W przypadku typu `string`jest to równoznaczne z `chr&`.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem, [Aby uzyskać przykład](#at) sposobu deklarowania i używania `reference`.

## <a name="rend"></a>basic_string:: rend

Zwraca iterator, który odnosi się do lokalizacji następującej po ostatnim elemencie w ciągu odwróconym.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Wartość zwrócona

Iterator odwrotnego dostępu swobodnego, który odnosi się do lokalizacji po ostatnim elemencie w ciągu odwróconym.

### <a name="remarks"></a>Uwagi

`rend` jest używany z odwróconym ciągiem, tak jak [koniec](#end) jest używany z ciągiem.

Jeśli wartość zwracana `rend` jest przypisana do `const_reverse_iterator`, nie można zmodyfikować obiektu ciągu. Jeśli wartość zwracana `rend` jest przypisana do `reverse_iterator`, można zmodyfikować obiekt ciągu.

`rend` można użyć do sprawdzenia, czy iterator odwrotny osiągnął koniec ciągu.

Nie należy wywoływać wartości zwracanej przez `rend`.

### <a name="example"></a>Przykład

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="replace"></a>basic_string:: Replace

Zamienia elementy w ciągu w określonej pozycji z określonymi znakami lub znakami skopiowanymi z innych zakresów lub ciągów lub ciągów języka C.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*str*\
Ciąg, który ma być źródłem znaków dla ciągu operandu.

*position_1*\
Indeks ciągu operandu, w którym rozpoczyna się zamienianie.

*number_1*\
Maksymalna liczba znaków, które mają zostać zastąpione w ciągu operandu.

*position_2*\
Indeks ciągu parametru, w którym rozpoczyna się kopiowanie.

*number_2*\
Maksymalna liczba znaków do użycia na podstawie parametru C-String.

\ *PTR*
Ciąg C, który ma być źródłem znaków dla ciągu operandu.

*char_value*\
Znak, który ma zostać skopiowany do ciągu operandu.

*first0*\
Iterator odnoszący się do pierwszego znaku, który ma zostać usunięty w ciągu operandu.

*last0*\
Iterator odnoszący się do ostatniego znaku, który ma zostać usunięty w ciągu operandu.

*pierwszy*\
Iterator, const_pointer lub const_iterator odnoszący się do pierwszego znaku, który ma być kopiowany w ciągu parametru.

*ostatni*\
Iterator, const_pointer lub const_iterator odnoszący się do ostatniego znaku, który ma zostać skopiowany w ciągu parametru.

*liczba*\
Liczba przypadków, gdy *char_value* jest kopiowana do ciągu operandu.

### <a name="return-value"></a>Wartość zwrócona

Ciąg operandu z wykonanym zastąpieniem.

### <a name="example"></a>Przykład

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="reserve"></a>basic_string:: Reserve

Ustawia pojemność ciągu na liczbę, która jest co najmniej równa podanej liczbie.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba znaków, dla których jest rezerwowana pamięć.

### <a name="remarks"></a>Uwagi

Posiadanie wystarczającej pojemności jest ważne, ponieważ ponowne alokacje to proces czasochłonny i unieważnia wszystkie odwołania, wskaźniki i Iteratory odwołujące się do znaków w ciągu.

Koncepcja pojemności dla obiektów typu String jest taka sama jak w przypadku obiektów typu Vector. W przeciwieństwie do wektora, funkcja członkowska `reserve` może zostać wywołana w celu zmniejszenia pojemności obiektu. Żądanie jest niewiążące i może być niewykonane. Ponieważ wartością domyślną dla parametru jest zero, wywołanie `reserve` jest żądaniem niewiążącym do zmniejszenia pojemności ciągu, aby dopasować liczbę znaków w ciągu. Pojemność nigdy nie zmniejszyła się poniżej bieżącej liczby znaków.

Wywoływanie `reserve` jest jedynym możliwym sposobem zmniejszenia pojemności ciągu. Jednak jak wspomniano powyżej, to żądanie jest niewiążące i może nie wystąpić.

### <a name="example"></a>Przykład

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="resize"></a>basic_string:: zmiana rozmiaru

Określa nowy rozmiar ciągu, dołączając lub wymazywając elementy zgodnie z wymaganiami.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>Parametry

*liczba*\
Nowy rozmiar ciągu.

*char_value*\
Wartość, która dołącza znaki, jest inicjowana przy użyciu, jeśli wymagane są dodatkowe elementy.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar uzyskany przekracza maksymalną liczbę znaków, formularz zgłosi `length_error`.

### <a name="example"></a>Przykład

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="reverse_iterator"></a>basic_string:: reverse_iterator

Typ, który zawiera odwołanie do elementu przechowywanego w ciągu.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Uwagi

Typ `reverse_iterator` może służyć do modyfikacji wartości znaku i służy do iteracji ciągu w odwrotnej postaci.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem dla [rbegin](#rbegin) , aby zapoznać się z przykładem sposobu deklarowania i używania `reverse_iterator`.

## <a name="rfind"></a>basic_string:: rfind

Wyszukuje ciąg w kierunku do tyłu dla pierwszego wystąpienia podciągu, który odpowiada określonej sekwencji znaków.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Wartość znaku, dla której funkcja członkowska ma być wyszukiwana.

\ *przesunięcia*
Indeks pozycji, w której ma zostać rozpoczęte wyszukiwanie.

\ *PTR*
Ciąg języka C, dla którego funkcja członkowska ma być wyszukiwana.

*liczba*\
Liczba znaków, która jest odliczana od pierwszego znaku w ciągu C, dla którego funkcja członkowska ma być wyszukiwana.

*str*\
Ciąg, dla którego funkcja członkowska ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwrócona

Indeks ostatniego wystąpienia podczas przeszukiwania do tyłu pierwszego znaku podciągu w przypadku powodzenia; w przeciwnym razie `npos`.

### <a name="example"></a>Przykład

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="shrink_to_fit"></a>basic_string:: shrink_to_fit

Odrzuca nadmiarową pojemność ciągu.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska eliminuje niepotrzebne magazyny w kontenerze.

## <a name="size"></a>basic_string:: size

Zwraca bieżącą liczbę elementów w ciągu.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Wartość zwrócona

Długość ciągu.

### <a name="example"></a>Przykład

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="size_type"></a>basic_string:: size_type

Typ liczby całkowitej bez znaku, który może reprezentować liczbę elementów i indeksów w ciągu.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>Uwagi

jest to równoważne `allocator_type::size_type`.

W przypadku typu `string`jest to równoznaczne z `size_t`.

### <a name="example"></a>Przykład

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="substr"></a>basic_string:: substr

Kopiuje podciąg z co najwyżej określoną liczbę znaków z ciągu rozpoczynającego się od określonej pozycji.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

\ *przesunięcia*
Indeks lokalizowania elementu na pozycji, z której jest wykonywana kopia ciągu, z wartością domyślną 0.

*liczba*\
Liczba znaków, które mają być skopiowane, jeśli są obecne.

### <a name="return-value"></a>Wartość zwrócona

Obiekt podciągu, który jest kopią elementów argumentu ciągu rozpoczynającego się w pozycji określonej przez pierwszy argument.

### <a name="example"></a>Przykład

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="swap"></a>basic_string:: swap

Wymiana zawartości dwóch ciągów.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*str*\
Ciąg źródłowy, którego elementy mają być wymieniane z tymi w ciągu docelowym.

### <a name="remarks"></a>Uwagi

Jeśli zamieniane ciągi mają ten sam obiekt alokatora, `swap` funkcja członkowska:

- Występuje w czasie stałym.

- Nie zgłasza wyjątków.

- Unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch ciągach.

W przeciwnym razie wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do liczby elementów w dwóch kontrolowanej sekwencji.

### <a name="example"></a>Przykład

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="traits_type"></a>basic_string:: traits_type

Typ cech znaków elementów przechowywanych w ciągu.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla drugiego parametru szablonu `Traits`.

Dla typu `string`jest to odpowiednik **char_traits\<char >** .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [kopiowania](../standard-library/char-traits-struct.md#copy) , aby zapoznać się z przykładem sposobu deklarowania i używania `traits_type`.

## <a name="value_type"></a>basic_string:: value_type

Typ, który reprezentuje typ znaków przechowywanych w ciągu.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Jest równoważne `traits_type::char_type` i jest odpowiednikiem **char** dla obiektów typu `string`.

### <a name="example"></a>Przykład

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>Zobacz też

[\<ciąg >](../standard-library/string.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
