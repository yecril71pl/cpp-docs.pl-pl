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
ms.openlocfilehash: 3d707ff963170b6b4f14ad1f04e9420b8062b520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366703"
---
# <a name="char_traits-struct"></a>char_traits — Struktura

Struktura char_traits opisuje atrybuty skojarzone ze znakiem.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ danych elementu.

## <a name="remarks"></a>Uwagi

Struktura szablonu opisuje różne cechy znaków `CharType`dla typu . Szablon klasy [basic_string,](../standard-library/basic-string-class.md) a także kilka szablonów klas iostream, w tym [basic_ios,](../standard-library/basic-ios-class.md)używają tych `CharType`informacji do manipulowania elementami typu. Taki typ elementu nie może wymagać wyraźnej konstrukcji lub zniszczenia. Musi dostarczyć domyślny konstruktor, konstruktor kopii i operator przypisania z oczekiwaną semantyką. Kopia bitowa musi mieć taki sam efekt jak przypisanie. Żadna z funkcji członkowskich struct char_traits może zgłaszać wyjątki.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ znaku.|
|[Int_type](#int_type)|Typ liczby całkowitej, który może `char_type` reprezentować znak typu lub znak końca pliku (EOF).|
|[off_type](#off_type)|Typ liczby całkowitej, który może reprezentować przesunięcia między pozycjami w strumieniu.|
|[pos_type](#pos_type)|Typ liczby całkowitej, który może reprezentować pozycje w strumieniu.|
|[state_type](#state_type)|Typ reprezentujący stan konwersji w przypadku znaków wielobajtowych w strumieniu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Przypisać](#assign)|Przypisuje jedną wartość znaku do innej.|
|[Porównać](#compare)|Porównuje do określonej liczby znaków w dwóch ciągach.|
|[Kopii](#copy)|Kopiuje określoną liczbę znaków z jednego ciągu do drugiego. Przestarzałe. Zamiast [tego użyj char_traits::_Copy_s.](#copy_s)|
|[_Copy_s](#copy_s)|Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.|
|[eof](#eof)|Zwraca znak końca pliku (EOF).|
|[Eq](#eq)|Sprawdza, `char_type` czy dwa znaki są równe.|
|[eq_int_type](#eq_int_type)|Sprawdza, czy dwa `int_type`znaki reprezentowane jako s są równe.|
|[find](#find)|Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.|
|[Długość](#length)|Zwraca długość ciągu.|
|[Por](#lt)|Sprawdza, czy jeden znak jest mniejszy niż inny.|
|[Przenieść](#move)|Kopiuje określoną liczbę znaków w sekwencji do innej, możliwe nakładające się sekwencji. Przestarzałe. Zamiast [tego użyj char_traits::_Move_s.](#move_s)|
|[_Move_s](#move_s)|Kopiuje określoną liczbę znaków w sekwencji do innej, możliwe nakładające się sekwencji.|
|[not_eof](#not_eof)|Sprawdza, czy znak jest znakiem końca pliku (EOF).|
|[to_char_type](#to_char_type)|Konwertuje `int_type` znak na `char_type` odpowiedni znak i zwraca wynik.|
|[to_int_type](#to_int_type)|Konwertuje `char_type` znak na `int_type` odpowiedni znak i zwraca wynik.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ciągu

**Przestrzeń nazw:** std

## <a name="char_traitsassign"></a><a name="assign"></a>char_traits::przypisywanie

Przypisuje jedną wartość znaku do innej lub do zakresu elementów w ciągu.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Parametry

**_** *CharFrom* Znak, którego wartość ma być przypisana.

*_CharTo*\
Element, który ma być przypisany wartość znaku.

*strTo*\
Tablica znaków lub znaków, których początkowe elementy mają być przypisane wartości znaków.

*_Num*\
Liczba elementów, które mają być przypisane wartości.

### <a name="return-value"></a>Wartość zwracana

Funkcja drugiego elementu członkowskiego zwraca wskaźnik do ciągu, którego pierwsze *_Num* elementy zostały przypisane wartości *_CharFrom*.

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

## <a name="char_traitschar_type"></a><a name="char_type"></a>char_traits::char_type

Typ znaku.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

### <a name="example"></a>Przykład

Zobacz przykład [kopiowania,](#copy) aby uzyskać przykład `char_type`sposobu deklarowania i używania pliku .

## <a name="char_traitscompare"></a><a name="compare"></a>char_traits::porównaj

Porównuje do określonej liczby znaków w dwóch ciągach.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*str1*\
Pierwszy z dwóch ciągów, które mają być porównywane ze sobą.

*str2*\
Drugi z dwóch ciągów, które mają być porównywane ze sobą.

*_Num*\
Liczba elementów w ciągach do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość ujemna, jeśli pierwszy ciąg jest mniejszy niż drugi ciąg, 0, jeśli dwa ciągi są równe, lub wartość dodatnia, jeśli pierwszy ciąg jest większy niż drugi ciąg.

### <a name="remarks"></a>Uwagi

Porównanie ciągów jest element po elemencie, najpierw testowanie równości, a następnie, jeśli para elementów w testach sekwencji nie jest równa, są testowane dla mniej niż.

Jeśli dwa ciągi porównać równe w zakresie, ale jeden jest dłuższy niż drugi, a następnie krótszy z dwóch jest mniejsza niż dłuższy.

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

## <a name="char_traitscopy"></a><a name="copy"></a>char_traits::copy

Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne. Zamiast tego należy rozważyć użycie [char_traits::_Copy_s.](#copy_s)

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Element na początku ciągu lub tablicy znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków do skopiowania.

*_Num*\
Liczba elementów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element skopiowany do zestawu ciągów lub znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Sekwencje znaków źródłowych i docelowych nie mogą się nakładać.

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

## <a name="char_traits_copy_s"></a><a name="copy_s"></a>char_traits::_Copy_s

Kopiuje określoną liczbę znaków z jednego ciągu do drugiego.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*Dest*\
Zestaw ciągów lub znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

*dest_size*\
Wielkość *dest*. Jeśli `char_type` jest **char**, a następnie ten rozmiar jest w bajtach. Jeśli `char_type` jest **wchar_t**, to ten rozmiar jest w słowach.

*_From*\
Ciąg źródłowy lub tablica znaków do skopiowania.

*Liczba*\
Liczba elementów do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zestaw ciągów lub znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Sekwencje znaków źródłowych i docelowych nie mogą się nakładać.

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

## <a name="char_traitseof"></a><a name="eof"></a>char_traits::eof

Zwraca znak końca pliku (EOF).

```cpp
static int_type eof();
```

### <a name="return-value"></a>Wartość zwracana

Znak EOF.

### <a name="remarks"></a>Uwagi

Wartość reprezentująca koniec pliku (na przykład EOF lub WEOF).

Standard C++ stwierdza, że ta wartość `char_type` nie może odpowiadać prawidłowej wartości. Kompilator Microsoft C++ wymusza to ograniczenie dla **typu char**, ale nie dla **typu wchar_t**. Prezentuje to poniższy przykład.

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

## <a name="char_traitseq"></a><a name="eq"></a>char_traits::eq

Sprawdza, `char_type` czy dwa znaki są równe.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwszy z dwóch znaków, które mają być testowane pod kątem równości.

*_Ch2*\
Drugi z dwóch znaków, które mają być testowane pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli pierwszy znak jest równy drugiemu znakowi; w przeciwnym razie **false**.

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

## <a name="char_traitseq_int_type"></a><a name="eq_int_type"></a>char_traits::eq_int_type

Sprawdza, czy dwa `int_type`znaki reprezentowane jako s są równe, czy nie.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwszy z dwóch znaków, które mają `int_type`być testowane pod kątem równości jako s.

*_Ch2*\
Drugi z dwóch znaków, które mają `int_type`być testowane pod kątem równości jako s.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli pierwszy znak jest równy drugiemu znakowi; w przeciwnym razie **false**.

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

## <a name="char_traitsfind"></a><a name="find"></a>char_traits::znajdź

Wyszukuje pierwsze wystąpienie określonego znaku w zakresie znaków.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*Str*\
Pierwszy znak w ciągu do przeszukania.

*_Num*\
Liczba pozycji, licząc od pierwszego, w zakresie, który ma być przeszukiwany.

*_ch*\
Postać, która ma być wyszukiwana w zakresie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pierwszego wystąpienia określonego znaku w zakresie, jeśli zostanie znaleziony dopasowanie; w przeciwnym razie wskaźnik zerowy.

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

## <a name="char_traitsint_type"></a><a name="int_type"></a>char_traits::int_type

Typ liczby całkowitej, który może `char_type` reprezentować znak typu lub znak końca pliku (EOF).

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Uwagi

Musi istnieć możliwość wpisania rzutowania `int_type` wartości `CharType` typu, `CharType` a następnie z powrotem do bez zmiany oryginalnej wartości.

### <a name="example"></a>Przykład

Zobacz przykład [eq_int_type](#eq_int_type) na przykład jak zadeklarować i `int_type`używać .

## <a name="char_traitslength"></a><a name="length"></a>char_traits::długość

Zwraca długość ciągu.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Parametry

*Str*\
Ciąg C, którego długość ma być mierzona.

### <a name="return-value"></a>Wartość zwracana

Liczba mierzonych elementów w sekwencji, z wyłączeniem zerowego terminatora.

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

## <a name="char_traitslt"></a><a name="lt"></a>char_traits::lt

Sprawdza, czy jeden znak jest mniejszy niż inny.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Parametry

*_Ch1*\
Pierwszy z dwóch znaków, które mają być testowane dla mniej niż.

*_Ch2*\
Drugi z dwóch znaków, które mają być testowane dla mniej niż.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli pierwszy znak jest mniejszy niż drugi znak; w przeciwnym razie **false**.

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

## <a name="char_traitsmove"></a><a name="move"></a>char_traits::przenieść

Kopiuje określoną liczbę znaków w sekwencji do innej, ewentualnie nakładającej się sekwencji.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne. Zamiast tego należy rozważyć użycie [char_traits::_Move_s.](#move_s)

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Parametry

*_To*\
Element na początku ciągu lub tablicy znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków do skopiowania.

*_Num*\
Liczba elementów do skopiowania z ciągu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element *_To* skopiowany do zestawu ciągów lub znaków przeznaczonych do odbierania skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Źródło i miejsce docelowe mogą się pokrywać.

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

## <a name="char_traits_move_s"></a><a name="move_s"></a>char_traits::_Move_s

Kopiuje określoną liczbę znaków w sekwencji do innej, ewentualnie nakładającej się sekwencji.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Parametry

*Dest*\
Element na początku ciągu lub tablicy znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

*dest_size*\
Wielkość *dest*. Jeśli `char_type` jest **char**, to jest w bajtach. Jeśli `char_type` jest **wchar_t**, to jest to w słowach.

*_From*\
Element na początku ciągu źródłowego lub tablicy znaków do skopiowania.

*Liczba*\
Liczba elementów do skopiowania z ciągu źródłowego.

### <a name="return-value"></a>Wartość zwracana

Pierwszy element *dest* kopiowane do ciągu lub tablicy znaków przeznaczony do odbierania skopiowanej sekwencji znaków.

### <a name="remarks"></a>Uwagi

Źródło i miejsce docelowe mogą się pokrywać.

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

## <a name="char_traitsnot_eof"></a><a name="not_eof"></a>char_traits::not_eof

Sprawdza, czy znak nie jest znakiem końca pliku (EOF), czy jest znakiem EOF.

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak reprezentowany jako `int_type` testowany pod kątem tego, czy jest to znak EOF, czy nie.

### <a name="return-value"></a>Wartość zwracana

Reprezentacja `int_type` testowanego znaku, jeśli `int_type` znak nie jest równy postaci znaku EOF.

Jeśli wartość `int_type` znaku jest równa `int_type` wartości EOF, wówczas **wartość false**.

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

## <a name="char_traitsoff_type"></a><a name="off_type"></a>char_traits::off_type

Typ liczby całkowitej, który może reprezentować przesunięcia między pozycjami w strumieniu.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Uwagi

Typ jest podpisaną całkowitej liczby, która opisuje obiekt, który może przechowywać przesunięcie bajtu zaangażowanych w różnych operacji pozycjonowania strumienia. Zazwyczaj jest synonimem [streamoff](../standard-library/ios-typedefs.md#streamoff), ale ma zasadniczo te same właściwości, jak ten typ.

## <a name="char_traitspos_type"></a><a name="pos_type"></a>char_traits::p_type

Typ liczby całkowitej, który może reprezentować pozycje w strumieniu.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może przechowywać wszystkie informacje potrzebne do przywrócenia dowolnego wskaźnika położenia pliku w strumieniu. Zazwyczaj jest synonimem [streampos](../standard-library/ios-typedefs.md#streampos), ale w każdym przypadku ma zasadniczo te same właściwości, jak ten typ.

## <a name="char_traitsstate_type"></a><a name="state_type"></a>char_traits::state_type

Typ reprezentujący stan konwersji dla znaków wielobajtowych w strumieniu.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Uwagi

Typ opisuje obiekt, który może reprezentować stan konwersji. Jest to zazwyczaj synonim `mbstate_t`, ale w każdym przypadku ma zasadniczo takie same właściwości jak tego typu.

## <a name="char_traitsto_char_type"></a><a name="to_char_type"></a>char_traits::to_char_type

Konwertuje `int_type` znak na `char_type` odpowiedni znak i zwraca wynik.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak, `int_type` który ma być `char_type`reprezentowany jako .

### <a name="return-value"></a>Wartość zwracana

Znak `char_type` odpowiadający `int_type` znakowi.

Wartość *_Ch,* które nie mogą być reprezentowane jako takie daje nieokreślony wynik.

### <a name="remarks"></a>Uwagi

Operacje konwersji [to_int_type](#to_int_type) i `to_char_type` są odwrotne do siebie, tak, że:

`to_int_type`( `to_char_type` ( *x* ) ) == *x*

dla `int_type` każdego *x* i

`to_char_type`( `to_int_type` ( *x* ) ) == *x*

dla `char_type` każdego *x*.

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

## <a name="char_traitsto_int_type"></a><a name="to_int_type"></a>char_traits::to_int_type

Konwertuje `char_type` znak na `int_type` odpowiedni znak i zwraca wynik.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak, `char_type` który ma być `int_type`reprezentowany jako .

### <a name="return-value"></a>Wartość zwracana

Znak `int_type` odpowiadający `char_type` znakowi.

### <a name="remarks"></a>Uwagi

Operacje `to_int_type` konwersji i [to_char_type](#to_char_type) są odwrotne do siebie, tak, że:

`to_int_type`( `to_char_type` ( *x* ) ) == *x*

dla `int_type` każdego *x*, i

`to_char_type`( `to_int_type` ( *x* ) ) == *x*

dla `char_type` każdego *x*.

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
