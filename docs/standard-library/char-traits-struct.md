---
title: char_traits — Struktura
ms.date: 05/07/2019
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: 834572e96d9d8c19ae5d75a57dfa6c0053ae0ec5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222605"
---
# <a name="char_traits-struct"></a>char_traits — Struktura

Struktura char_traits zawiera opis atrybutów skojarzonych ze znakiem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ danych elementu.

## <a name="remarks"></a>Uwagi

Struktura szablonu opisuje różne cechy znakowe typu `CharType` . Szablon klasy [basic_string](../standard-library/basic-string-class.md) jak również kilka szablonów klas iostream, w tym [basic_ios](../standard-library/basic-ios-class.md), te informacje służą do manipulowania elementami typu `CharType` . Taki typ elementu nie może wymagać jawnej konstrukcji ani zniszczenia. Musi dostarczyć Konstruktor domyślny, Konstruktor kopiujący i operator przypisania z oczekiwaną semantyką. Kopia bitowa musi mieć ten sam skutek jak przypisanie. Żadna z funkcji Członkowskich struktury char_traits nie może generować wyjątków.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ znaku.|
|[int_type](#int_type)|Typ liczby całkowitej, który może reprezentować znak typu `char_type` lub znak końca pliku (EOF).|
|[off_type](#off_type)|Typ liczby całkowitej, który może reprezentować przesunięcia między pozycjami w strumieniu.|
|[pos_type](#pos_type)|Typ liczby całkowitej, który może reprezentować pozycje w strumieniu.|
|[state_type](#state_type)|Typ, który reprezentuje stan konwersji dla znaków wielobajtowych w strumieniu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[przypisać](#assign)|Przypisuje jedną wartość znaku do innej.|
|[porównaniu](#compare)|Porównuje do określonej liczby znaków w dwóch ciągach.|
|[kopiowane](#copy)|Kopiuje określoną liczbę znaków z jednego ciągu do drugiego. Przestarzałe. Zamiast tego użyj [char_traits:: _Copy_s](#copy_s) .|
|[_Copy_s](#copy_s)|Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.|
|[końca](#eof)|Zwraca znak końca pliku (EOF).|
|[eq](#eq)|Testuje, czy dwa `char_type` znaki są równe.|
|[eq_int_type](#eq_int_type)|Testuje, czy dwa znaki reprezentowane jako `int_type` s są równe.|
|[find](#find)|Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.|
|[Długość](#length)|Zwraca długość ciągu.|
|[lt](#lt)|Testuje, czy jeden znak jest mniejszy niż inny.|
|[Przenieś](#move)|Kopiuje określoną liczbę znaków w sekwencji do innej, możliwego nakładania się sekwencji. Przestarzałe. Zamiast tego użyj [char_traits:: _Move_s](#move_s) .|
|[_Move_s](#move_s)|Kopiuje określoną liczbę znaków w sekwencji do innej, możliwego nakładania się sekwencji.|
|[not_eof](#not_eof)|Testuje, czy znak jest znakiem końca pliku (EOF).|
|[to_char_type](#to_char_type)|Konwertuje `int_type` znak na odpowiedni `char_type` znak i zwraca wynik.|
|[to_int_type](#to_int_type)|Konwertuje `char_type` znak na odpowiedni `int_type` znak i zwraca wynik.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<string>

**Przestrzeń nazw:** std

## <a name="char_traitsassign"></a><a name="assign"></a>char_traits:: Assign

Przypisuje jedną wartość znaku do innej lub do zakresu elementów w ciągu.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Parametry

**_** *CharFrom* znak, którego wartość ma zostać przypisana.

*_CharTo*\
Element, do którego ma zostać przypisana wartość znaku.

*strTo*\
Ciąg lub tablica znaków, której początkowe elementy mają być przypisane do wartości znakowych.

*_Num*\
Liczba elementów, które mają być przypisane do wartości.

### <a name="return-value"></a>Wartość zwracana

Druga funkcja członkowska zwraca wskaźnik do ciągu, którego pierwsze *_Num* elementy przypisały wartości *_CharFrom*.

### <a name="example"></a>Przykład

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_traitschar_type"></a><a name="char_type"></a>char_traits:: char_type

Typ znaku.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType` .

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [kopiowania](#copy) , aby zapoznać się z przykładem sposobu deklarowania i używania `char_type` .

## <a name="char_traitscompare"></a><a name="compare"></a>char_traits:: Compare

Porównuje do określonej liczby znaków w dwóch ciągach.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*str1*\
Pierwsze dwa ciągi, które mają być porównywane ze sobą.

*str2*\
Drugi z dwóch ciągów, które mają być porównywane ze sobą.

*_Num*\
Liczba elementów w ciągach, które mają być porównane.

### <a name="return-value"></a>Wartość zwracana

Wartość ujemna, jeśli pierwszy ciąg jest mniejszy niż drugi ciąg, 0, jeśli dwa ciągi są równe lub wartość dodatnia, jeśli pierwszy ciąg jest większy niż drugi ciąg.

### <a name="remarks"></a>Uwagi

Porównanie między ciągami jest elementami elementu przez element, pierwsze testy pod kątem równości, a następnie, jeśli para elementów w testach sekwencji nie jest równa się, są testowane dla mniejszej niż.

Jeśli dwa ciągi są porównywane nad zakresem, ale jeden jest dłuższy niż drugi, to krótszy z nich jest mniejszy niż dłuższy.

### <a name="example"></a>Przykład

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="char_traitscopy"></a><a name="copy"></a>char_traits:: Copy

Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne. Zamiast tego Rozważ użycie [char_traits:: _Copy_s](#copy_s) .

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Element na początku ciągu lub tablicy znaków, do którego odnoszą się skopiowane sekwencje znaków.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków, który ma zostać skopiowany.

*_Num*\
Liczba elementów, które mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element jest kopiowany do tablicy ciągów lub znaków przeznaczonych do odbioru skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Sekwencje znaków źródłowej i docelowej nie mogą nakładać się na siebie.

### <a name="example"></a>Przykład

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="char_traits_copy_s"></a><a name="copy_s"></a>char_traits:: _Copy_s

Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*dest*\
Ciąg lub tablica znaków przeznaczona do odbioru skopiowanej sekwencji znaków.

*dest_size*\
Rozmiar miejsca *docelowego*. Jeśli `char_type` jest **`char`** , ten rozmiar jest w bajtach. Jeśli `char_type` tak **`wchar_t`** , ten rozmiar jest w wyrazach.

*_From*\
Ciąg źródłowy lub tablica znaków do skopiowania.

*liczbą*\
Liczba elementów, które mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Ciąg lub tablica znaków przeznaczona do odbioru skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Sekwencje znaków źródłowej i docelowej nie mogą nakładać się na siebie.

### <a name="example"></a>Przykład

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="char_traitseof"></a><a name="eof"></a>char_traits:: EOF

Zwraca znak końca pliku (EOF).

```cpp
static int_type eof();
```

### <a name="return-value"></a>Wartość zwracana

Znak EOF.

### <a name="remarks"></a>Uwagi

Wartość, która reprezentuje koniec pliku (na przykład EOF lub WEOF).

Standard C++ wskazuje, że ta wartość nie może odpowiadać prawidłowej `char_type` wartości. Kompilator języka Microsoft C++ wymusza to ograniczenie dla typu **`char`** , ale nie dla typu **`wchar_t`** . Prezentuje to poniższy przykład.

### <a name="example"></a>Przykład

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="char_traitseq"></a><a name="eq"></a>char_traits:: EQ

Testuje, czy dwa `char_type` znaki są równe.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwsze dwa znaki do przetestowania pod kątem równości.

*_Ch2*\
Drugi z dwóch znaków do sprawdzenia pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli pierwszy znak jest równy drugiemu znakowi; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="char_traitseq_int_type"></a><a name="eq_int_type"></a>char_traits:: eq_int_type

Testuje, czy dwa znaki reprezentowane jako `int_type` s są równe, czy nie.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwszy z dwóch znaków do przetestowania pod kątem równości jako `int_type` s.

*_Ch2*\
Drugi z dwóch znaków do przetestowania pod kątem równości jako `int_type` s.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli pierwszy znak jest równy drugiemu znakowi; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="char_traitsfind"></a><a name="find"></a>char_traits:: find

Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*str*\
Pierwszy znak w ciągu, który ma być przeszukiwany.

*_Num*\
Liczba pozycji, licząc od pierwszej, w zakresie, który ma być przeszukiwany.

*_Ch*\
Znak, który ma być wyszukiwany w zakresie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego wystąpienia określonego znaku w zakresie, jeśli zostanie znalezione dopasowanie; w przeciwnym razie wskaźnik o wartości null.

### <a name="example"></a>Przykład

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="char_traitsint_type"></a><a name="int_type"></a>char_traits:: int_type

Typ liczby całkowitej, który może reprezentować znak typu `char_type` lub znak końca pliku (EOF).

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Uwagi

Musi być możliwe wpisanie rzutowania wartości typu, `CharType` Aby `int_type` wrócić do `CharType` niezmienionej wartości pierwotnej.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [eq_int_type](#eq_int_type) , aby zapoznać się z przykładem sposobu deklarowania i używania `int_type` .

## <a name="char_traitslength"></a><a name="length"></a>char_traits:: length

Zwraca długość ciągu.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Parametry

*str*\
Ciąg języka C, którego długość ma być mierzona.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w sekwencji mierzonych, które nie obejmują terminatora o wartości null.

### <a name="example"></a>Przykład

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="char_traitslt"></a><a name="lt"></a>char_traits:: lt

Testuje, czy jeden znak jest mniejszy niż inny.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwsze dwa znaki do przetestowania mniejsze niż.

*_Ch2*\
Dwa z dwóch znaków do przetestowania mniejsze niż.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli pierwszy znak jest mniejszy od drugiego znaku; w przeciwnym razie **`false`** .

### <a name="example"></a>Przykład

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="char_traitsmove"></a><a name="move"></a>char_traits:: Move

Kopiuje określoną liczbę znaków w sekwencji do innej, która może nakładać się na sekwencję.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne. Zamiast tego Rozważ użycie [char_traits:: _Move_s](#move_s) .

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Element na początku ciągu lub tablicy znaków, do którego odnoszą się skopiowane sekwencje znaków.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków, który ma zostać skopiowany.

*_Num*\
Liczba elementów, które mają zostać skopiowane z ciągu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element *_to* kopiowany do tablicy ciągów lub tablic znaków przeznaczonych do odbioru skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Źródło i miejsce docelowe mogą się nakładać.

### <a name="example"></a>Przykład

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="char_traits_move_s"></a><a name="move_s"></a>char_traits:: _Move_s

Kopiuje określoną liczbę znaków w sekwencji do innej, która może nakładać się na sekwencję.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*dest*\
Element na początku ciągu lub tablicy znaków, do którego odnoszą się skopiowane sekwencje znaków.

*dest_size*\
Rozmiar miejsca *docelowego*. Jeśli `char_type` jest **`char`** , to w bajtach. Jeśli `char_type` tak **`wchar_t`** , to jest to słowo.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków, który ma zostać skopiowany.

*liczbą*\
Liczba elementów, które mają zostać skopiowane z ciągu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element *docelowy* został skopiowany do tablicy ciągów lub tablic znaków przeznaczonych do odbioru skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Źródło i miejsce docelowe mogą się nakładać.

### <a name="example"></a>Przykład

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="char_traitsnot_eof"></a><a name="not_eof"></a>char_traits:: not_eof

Testuje, czy znak nie jest znakiem końca pliku (EOF) lub jest EOF.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak reprezentowany jako `int_type` do przetestowania, czy jest to znak EOF, czy nie.

### <a name="return-value"></a>Wartość zwracana

`int_type`Reprezentacja testowanego znaku, jeśli `int_type` znak nie jest równy znakowi EOF.

Jeśli wartość znaku `int_type` jest równa `int_type` wartości EOF, to **`false`** .

### <a name="example"></a>Przykład

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="char_traitsoff_type"></a><a name="off_type"></a>char_traits:: off_type

Typ liczby całkowitej, który może reprezentować przesunięcia między pozycjami w strumieniu.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Uwagi

Typ to liczba całkowita ze znakiem, która opisuje obiekt, który może przechowywać przesunięcie bajtów związane z różnymi operacjami pozycjonowania strumienia. Jest zazwyczaj synonimem dla [streamoff —](../standard-library/ios-typedefs.md#streamoff), ale ma zasadniczo te same właściwości, co ten typ.

## <a name="char_traitspos_type"></a><a name="pos_type"></a>char_traits::p os_type

Typ liczby całkowitej, który może reprezentować pozycje w strumieniu.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może przechowywać wszystkie informacje, które są konieczne do przywrócenia dowolnego wskaźnika położenia pliku w strumieniu. Jest zazwyczaj synonimem dla [streampos](../standard-library/ios-typedefs.md#streampos), ale w każdym przypadku ma zasadniczo te same właściwości, co ten typ.

## <a name="char_traitsstate_type"></a><a name="state_type"></a>char_traits:: state_type

Typ, który reprezentuje stan konwersji znaków wielobajtowych w strumieniu.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może reprezentować stan konwersji. Jest zazwyczaj synonimem dla `mbstate_t` , ale w każdym przypadku ma zasadniczo te same właściwości, co ten typ.

## <a name="char_traitsto_char_type"></a><a name="to_char_type"></a>char_traits:: to_char_type

Konwertuje `int_type` znak na odpowiedni `char_type` znak i zwraca wynik.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
`int_type`Znak, który ma być reprezentowany jako `char_type` .

### <a name="return-value"></a>Wartość zwracana

`char_type`Znak odpowiadający `int_type` znakowi.

Wartość *_Ch* , która nie może być reprezentowana w taki sposób, że daje nieokreślony wynik.

### <a name="remarks"></a>Uwagi

Operacje konwersji [to_int_type](#to_int_type) i `to_char_type` są odwrotnie do siebie, dzięki czemu:

`to_int_type`( `to_char_type` ( *x* )) = = *x*

dla dowolnego `int_type` *x* i

`to_char_type`( `to_int_type` ( *x* )) = = *x*

dla dowolnego `char_type` *x*.

### <a name="example"></a>Przykład

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="char_traitsto_int_type"></a><a name="to_int_type"></a>char_traits:: to_int_type

Konwertuje `char_type` znak na odpowiedni `int_type` znak i zwraca wynik.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
`char_type`Znak, który ma być reprezentowany jako `int_type` .

### <a name="return-value"></a>Wartość zwracana

`int_type`Znak odpowiadający `char_type` znakowi.

### <a name="remarks"></a>Uwagi

Operacje konwersji `to_int_type` i [to_char_type](#to_char_type) są odwrotnie do siebie, więc:

`to_int_type`( `to_char_type` ( *x* )) = = *x*

dla dowolnego `int_type` *x*i

`to_char_type`( `to_int_type` ( *x* )) = = *x*

dla dowolnego `char_type` *x*.

### <a name="example"></a>Przykład

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
