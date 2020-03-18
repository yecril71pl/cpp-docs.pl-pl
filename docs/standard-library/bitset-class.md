---
title: bitset — Klasa
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: a4771e9c2c48bfe9c4c09629278533b031d60979
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421941"
---
# <a name="bitset-class"></a>bitset — Klasa

Opisuje typ obiektu, który przechowuje sekwencję składającą się ze stałej liczby bitów, która zapewnia zwarty sposób utrzymywania flag dla zestawu elementów lub warunków. Klasa bitset obsługuje operacje na obiektach typu bitset, które zawierają kolekcję bitów i zapewniają stały dostęp do każdego bitu.

## <a name="syntax"></a>Składnia

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parametry

*N*\
Określa liczbę bitów w obiekcie bitset o niezerowej liczbie całkowitej typu `size_t`, która musi być znana w czasie kompilacji.

## <a name="remarks"></a>Uwagi

W przeciwieństwie do podobnej [klasy vector\<bool >](../standard-library/vector-bool-class.md), Klasa bitset nie ma iteratorów i nie jest kontenerem biblioteki C++ standardowej. Różni się także od wektorów\<bool > przez wyznaczony rozmiar, który jest ustalany w czasie kompilacji zgodnie z rozmiarem określonym przez parametr szablonu *n* , gdy **bitset\<N\>** jest zadeklarowana.

Bit jest ustawiony, jeśli jego wartość jest równa 1 i zresetowana, jeśli jej wartość wynosi 0. Aby przerzucić lub odwrócić bit, należy zmienić jego wartość z 1 na 0 lub z 0 na 1. *N* bitów w bitset są indeksowane wartości całkowite z przedziału od 0 do *N* -1, gdzie 0 indeksuje pierwszą pozycję bitową i *N* -1 ostatniej pozycji bitu.

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktorzy

|||
|-|-|
|[bitset](#bitset)|Konstruuje obiekt klasy `bitset\<N>` i inicjuje bity do zera, do określonej wartości lub do wartości uzyskanych z znaków w ciągu.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ, który jest synonimem typu danych **bool** i może służyć do odwoływania się do bitów elementów w `bitset`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[całą](#all)|Testuje wszystkie bity w tym `bitset`, aby określić, czy są one ustawione na **wartość true**.|
|[ile](#any)|Funkcja członkowska testuje, czy dowolny bit w sekwencji jest ustawiony na 1.|
|[count](#count)|Funkcja członkowska zwraca liczbę bitów ustawionych w sekwencji bitowej.|
|[stosowane](#flip)|Odwraca wartość wszystkich bitów w `bitset` lub odwraca pojedynczy bit na określonej pozycji.|
|[dawaj](#none)|Testuje, czy żaden bit nie został ustawiony na 1 w obiekcie `bitset`.|
|[zresetować](#reset)|Resetuje wszystkie bity w `bitset` do 0 lub resetuje bit w określonym położeniu do 0.|
|[set](#set)|Ustawia wszystkie bity w `bitset` na 1 lub ustawia bit w określonym położeniu na 1.|
|[zmienia](#size)|Zwraca liczbę bitów w obiekcie `bitset`.|
|[badan](#test)|Testuje, czy bit na określonej pozycji w `bitset` jest ustawiony na 1.|
|[to_string](#to_string)|Konwertuje obiekt `bitset` na reprezentację ciągu.|
|[to_ullong](#to_ullong)|Zwraca sumę wartości bitowych w `bitset` jako **unsigned long long**.|
|[to_ulong](#to_ulong)|Konwertuje obiekt `bitset` do **niepodpisanej długości** , która spowodowałaby wygenerowanie sekwencji bitów zawartych w przypadku użycia do zainicjowania `bitset`.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[odwoła](#reference)|Klasa proxy, która udostępnia odwołania do bitów zawartych w `bitset`, która jest używana do uzyskiwania dostępu do poszczególnych bitów i manipulowania nimi jako Klasa pomocnika dla `operator[]` klasy `bitset`.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](#op_neq)|Testuje `bitset` docelowy dla nierówności z określonym `bitset`.|
|[& operatora =](#op_and_eq)|Wykonuje bitową kombinację bitsets za pomocą operacji logicznej `AND`.|
|[< operatora <](#op_lshift)|Przenosi bity w `bitset` w lewo o określoną liczbę pozycji i zwraca wynik do nowej `bitset`.|
|[< operatora < =](#op_lshift_eq)|Przenosi bity w `bitset` w lewo o określoną liczbę pozycji i zwraca wynik do `bitset`dostosowanej.|
|[operator = =](#op_eq_eq)|Testuje `bitset` docelowy dla równości z określonym `bitset`.|
|[> operatora >](#op_rshift)|Przenosi bity w `bitset` w prawo o określoną liczbę pozycji i zwraca wynik do nowej `bitset`.|
|[> operatora > =](#op_rshift_eq)|Przenosi bity w `bitset` w prawo o określoną liczbę pozycji i zwraca wynik do `bitset`dostosowanej.|
|[zakład&#91;&#93;](#op_at)|Zwraca odwołanie do bitu na określonej pozycji w `bitset`, jeśli `bitset` można modyfikować. w przeciwnym razie zwraca wartość bitu w tym położeniu.|
|[operator ^ =](#op_xor_eq)|Wykonuje bitową kombinację bitsets z wyłączną operacją `OR`.|
|[operator&#124;=](#op_or_eq)|Wykonuje bitową kombinację bitsets z operacją `OR` włącznie.|
|[operator ~](#op_not)|Odwraca wszystkie bity w elemencie docelowym `bitset` i zwraca wynik.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[skrótu](#hash)||

### <a name="all"></a>całą

Testuje wszystkie bity w tym bitset, aby określić, czy są one ustawione na wartość true.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość PRAWDA, jeśli wszystkie bity w tym zestawie są spełnione. Zwraca **wartość false** , jeśli co najmniej jeden bity ma wartość false.

### <a name="any"></a>ile

Testuje, czy dowolny bit w sekwencji jest ustawiony na 1.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli dowolny bit w bitset jest ustawiony na 1; **Fałsz** , jeśli wszystkie bity są równe 0.

#### <a name="example"></a>Przykład

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a>bitset

Konstruuje obiekt klasy `bitset\<N>` i inicjuje bity do zera lub do określonej wartości lub do wartości uzyskanych z znaków w ciągu.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>Parametry

*val*\
Liczba całkowita bez znaku, której dwie reprezentacja podstawowa jest używana do inicjowania bitów w bitset.

*str*\
Ciąg zer i tych, których użyto do zainicjowania wartości bitowych bitset.

*_CStr*\
Ciąg w stylu C o wartości zero i te, które służą do inicjowania wartości bitowych bitset.

*_Pos*\
Pozycja znaku w ciągu, licząc od lewej do prawej i rozpoczynając od zera, służąca do inicjowania pierwszego bitu w bitset.

*liczba*\
Liczba znaków w ciągu, która jest używana do dostarczania wartości początkowych dla bitów w bitset.

*_Zero*\
Znak, który jest używany do reprezentowania wartości zero. Wartość domyślna to "0".

*_One*\
Znak, który jest używany do reprezentowania jednego. Wartość domyślna to "1".

#### <a name="remarks"></a>Uwagi

Trzy konstruktory mogą służyć do konstruowania obects `bitset\<N>`klasy:

- Pierwszy Konstruktor nie akceptuje żadnych parametrów, konstruuje obiekt klasy `bitset\<N>` i inicjuje wszystkie N bitów do wartości domyślnej równej zero.

- Drugi Konstruktor konstruuje obiekt klasy `bitset\<N>` i inicjuje bity przy użyciu pojedynczego **niepodpisanego parametru long long** .

- Trzeci Konstruktor konstruuje obiekt klasy `bitset\<N>`, inicjując N bitów do wartości, które odpowiadają znakom podanym w ciągu znaków w stylu c i. Wywoływanie konstruktora bez rzutowania ciągu na typ String: `bitset<5> b5("01011");`

Dostępne są również dwa szablony konstruktora:

- Pierwszy szablon konstruktora konstruuje obiekt klasy `bitset\<N>` i inicjuje bity z znaków dostarczonych w ciągu zera i. Jeśli dowolne znaki ciągu są inne niż 0 lub 1, Konstruktor zgłasza obiekt klasy [nieprawidłowy argument](../standard-library/invalid-argument-class.md). Jeśli określona pozycja ( *_Pos*) jest dłuższa niż długość ciągu, Konstruktor zgłosi obiekt klasy [out_of_range](../standard-library/out-of-range-class.md). Konstruktor ustawia tylko bity na pozycji *j* w bitset, dla którego znak w ciągu na pozycji `_Pos + j` ma wartość 1. Domyślnie *_Pos* jest równa 0.

- Drugi szablon konstruktora jest podobny do pierwszego, ale zawiera dodatkowy parametr (*Count*), który jest używany do określenia liczby bitów do zainicjowania. Ma także dwa parametry opcjonalne, *_Zero* i *_One*, co wskazuje, jaki znak w *str* ma być interpretowany tak, aby oznaczał odpowiednio 0 bitów i 1 bit.

#### <a name="example"></a>Przykład

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a>liczbą

Zwraca liczbę bitów ustawionych w sekwencji bitowej.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Wartość zwrócona

Liczba bitów ustawiona w sekwencji bitowej.

#### <a name="example"></a>Przykład

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a>element_type

Typ, który jest synonimem typu danych **bool** i może służyć do odwoływania się do bitów elementu w bitset.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>Przykład

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a>stosowane

Odwraca wartość wszystkich bitów w bitset lub odwraca pojedynczy bit na określonej pozycji.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja bitu, którego wartość ma zostać odwrócona.

#### <a name="return-value"></a>Wartość zwrócona

Kopia zmodyfikowanego bitset, dla którego wywołano funkcję członkowską.

#### <a name="remarks"></a>Uwagi

Druga funkcja członkowska zgłasza wyjątek [out_of_range](../standard-library/out-of-range-class.md) , jeśli pozycja określona jako parametr jest większa niż rozmiar *N* **bitset\<** *n* **>** którego bit został odwrócony.

#### <a name="example"></a>Przykład

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a>skrótu

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a>dawaj

Testuje, czy żaden bit nie został ustawiony na 1 w obiekcie bitset.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli nie ustawiono bitu w bitset na 1; **wartość false** , jeśli co najmniej jeden bit został ustawiony na 1.

#### <a name="example"></a>Przykład

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="op_neq"></a>operator! =

Testuje docelowy bitset dla nierówności z określonym bitset.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*prawa*\
Bitset, który ma zostać porównany z bitsetem docelowym dla nierówności.

#### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli bitsets są różne; **Fałsz** , jeśli są takie same.

#### <a name="remarks"></a>Uwagi

Bitsets musi mieć ten sam rozmiar, który ma być testowany pod kątem nierówności przez funkcję operatora składowej.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_and_eq"></a>&amp;operatora =

Wykonuje bitową kombinację bitsets za pomocą operacji logicznej `AND`.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*prawa*\
Bitset, który ma być połączony bitowy z bitsetem docelowym.

#### <a name="return-value"></a>Wartość zwrócona

Zmodyfikowana wartość docelowa bitset, która jest wynikiem operacji `AND` bitowej z bitset określoną jako parametr.

#### <a name="remarks"></a>Uwagi

Dwa bity połączone przez operator `AND` zwracają **wartość true** , jeśli każdy bit ma wartość true; w przeciwnym razie ich kombinacja zwraca **wartość false**.

Bitsets musi mieć ten sam rozmiar, aby można było łączyć bitowe z operatorem `AND` przez funkcję operatora elementu członkowskiego.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_lshift"></a>\<operatora \<

Przenosi bity w bitset do lewej określoną liczbę pozycji i zwraca wynik do nowego bitset.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Liczba pozycji po lewej stronie, które mają zostać przesunięte w bitset.

#### <a name="return-value"></a>Wartość zwrócona

Zmodyfikowany bitset z bitami przenoszonymi w lewo do wymaganej liczby pozycji.

#### <a name="remarks"></a>Uwagi

Funkcja operator elementu członkowskiego zwraca **bitset**( **\*this**) **< < = POS,** gdzie [<<=](#op_lshift_eq) przenosi bity w bitset do lewej określoną liczbę pozycji i zwraca wynik do bitsetu.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="op_lshift_eq"></a>&lt;&lt;operatora =

Przenosi bity w bitset do lewej określoną liczbę pozycji i zwraca wynik do obiektu bitset.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Liczba pozycji z lewej strony, które mają zostać przesunięte w bitset.

#### <a name="return-value"></a>Wartość zwrócona

Celem bitset zmodyfikowano, tak aby bity były przesunięte w lewo do wymaganej liczby pozycji.

#### <a name="remarks"></a>Uwagi

Jeśli nie istnieje element, który ma zostać przesunięty w położenie, funkcja czyści bit do wartości 0.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="op_eq_eq"></a>operator = =

Testuje docelowy bitset dla równości z określonym bitset.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*prawa*\
Bitset, który ma zostać porównany z bitsetem docelowym.

#### <a name="return-value"></a>Wartość zwrócona

**wartość true** , jeśli bitsets jest taka sama; **Fałsz** , jeśli są różne.

#### <a name="remarks"></a>Uwagi

Bitsets musi mieć ten sam rozmiar, który ma być testowany pod kątem równości przez funkcję operatora składowej.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_rshift"></a>&gt;operatora &gt;

Przenosi bity w bitset do prawej określonej liczby pozycji i zwraca wynik do nowego bitset.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Liczba pozycji z prawej strony, które mają zostać przesunięte w bitset.

#### <a name="return-value"></a>Wartość zwrócona

Nowy bitset, w którym bity zostały przesunięte w prawo do wymaganej liczby pozycji względem dostosowanej bitset.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="op_rshift_eq"></a>&gt;&gt;operatora =

Przenosi bity w bitset do prawej określonej liczby pozycji i zwraca wynik do obiektu bitset.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Liczba pozycji z prawej strony, które mają zostać przesunięte w bitset.

#### <a name="return-value"></a>Wartość zwrócona

Celem bitset zmodyfikowano, tak aby bity były przesunięte do odpowiedniej liczby pozycji.

#### <a name="remarks"></a>Uwagi

Jeśli nie istnieje element, który ma zostać przesunięty w położenie, funkcja czyści bit do wartości 0.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="op_at"></a>operator []

Zwraca odwołanie do bitu na określonej pozycji w bitset, jeśli bitset jest modyfikowalna; w przeciwnym razie zwraca wartość bitu w tym położeniu.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Położenie, w którym znajduje się bit w bitset.

#### <a name="remarks"></a>Uwagi

W przypadku zdefiniowania [\_iteratora\_debugowania poziomu\_](../standard-library/iterator-debug-level.md) jako 1 lub 2 w kompilacji wystąpi błąd czasu wykonywania w pliku wykonywalnym, jeśli próbujesz uzyskać dostęp do elementu poza granicami bitset. Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

#### <a name="example"></a>Przykład

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="op_xor_eq"></a>operator ^ =

Wykonuje bitową kombinację bitsets z wyłączną operacją `OR`.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*prawa*\
Bitset, który ma być połączony bitowy z bitsetem docelowym.

#### <a name="return-value"></a>Wartość zwrócona

Zmodyfikowana wartość docelowa bitset, która wynika z operacji bitowego `OR` wyłącznego z bitset określony jako parametr.

#### <a name="remarks"></a>Uwagi

Dwie bity połączone przez wyłączny operator **or** zwracają **wartość true** , jeśli co najmniej jeden z nich, ale nie oba, jest **prawdziwy**; w przeciwnym razie ich kombinacja zwraca **wartość false**.

Bitsets musi mieć taki sam rozmiar, aby można było łączyć bitowe z operatorem wyłącznego `OR` przez funkcję operatora elementu członkowskiego.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_or_eq"></a>operator&#124;=

Wykonuje bitową kombinację bitsets z operacją `OR` włącznie.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*prawa*\
Bitset, który ma być połączony bitowy z bitsetem docelowym.

#### <a name="return-value"></a>Wartość zwrócona

Zmodyfikowana wartość docelowa bitset, która jest wynikiem operacji bitowego `OR`, z bitsetem określonym jako parametr.

#### <a name="remarks"></a>Uwagi

Dwie bity połączone operatorem `OR` włącznie zwracają **wartość true** , jeśli co najmniej jeden z bitów ma **wartość true**; Jeśli obie bity mają **wartość false**, ich kombinacje zwracają **wartość false**.

Bitsets musi mieć ten sam rozmiar, aby można było łączyć bitowe z operatorem włącznego `OR` przez funkcję operatora elementu członkowskiego.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_not"></a>operator ~

Odwraca wszystkie bity w docelowym bitset i zwraca wynik.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Wartość zwrócona

Bitset z wszystkimi bitami odwracanymi w odniesieniu do dostosowanej bitset.

#### <a name="example"></a>Przykład

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a>odwoła

Klasa proxy, która udostępnia odwołania do bitów zawartych w bitset, która jest używana do uzyskiwania dostępu do poszczególnych bitów i manipulowania nimi jako Klasa pomocnika dla `operator[]` klasy bitset.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>Parametry

*val*\
Wartość obiektu typu **bool** , która ma być przypisana do bitu w bitset.

*_Bitref*\
Odwołanie do postaci *x [i]* do bitu na pozycji *i* w bitset *x*.

#### <a name="return-value"></a>Wartość zwrócona

Odwołanie do bitu w bitset określonym przez pozycję argumentu dla pierwszej, drugiej i piątej funkcji składowej klasy Reference oraz **wartości true** lub **false**, aby odzwierciedlić wartość zmodyfikowanego bitu w bitset dla trzeciej i czwartej funkcji składowej odwołania do klasy.

#### <a name="remarks"></a>Uwagi

Klasa `reference` istnieje tylko jako Klasa pomocnika dla `operator[]`bitset. Klasa członkowska opisuje obiekt, który może uzyskać dostęp do pojedynczego bitu w bitset. Niech *b* jest obiektem typu **bool**, *x* i *y* obiektów typu **bitset\<** *N* **>** *, i i* *j* prawidłowymi pozycjami w ramach takiego obiektu. Notacja *x [i]* odwołuje się do bitu na pozycji *i* w bitset *x*. Funkcje składowe klasy `reference` zapewniają w kolejności następujące operacje:

|Operacja|Definicja|
|---------------|----------------|
|*x*[*i*] = *b*|Przechowuje wartość logiczną *b* w pozycji bitowej *i* w bitset *x*.|
|*x*[*i*] = *y*[*j*]|Przechowuje wartość bitu *y*[ *j*] w pozycji bitowej *i* w bitset *x*.|
|*b* = ~ *x*[*i*]|Przechowuje przerzucaną wartość bit *x*[ *i*] w **bool** *b*.|
|*b* = *x*[*i*]|Przechowuje wartość bitu *x*[ *i*] w **bool** *b*.|
|*x*[*i*]. `flip`()|Przechowuje przerzucaną wartość bitu *x*[ *i*] z powrotem na pozycji bitowej *i* w *x*.|

#### <a name="example"></a>Przykład

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a>zresetować

Resetuje wszystkie bity w bitset do 0 lub resetuje bit w określonym położeniu do 0.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja bitu w bitset, która ma zostać zresetowana do wartości 0.

#### <a name="return-value"></a>Wartość zwrócona

Kopia elementu bitset, dla którego wywołano funkcję członkowską.

#### <a name="remarks"></a>Uwagi

Druga funkcja członkowska zgłasza wyjątek [out_of_range](../standard-library/out-of-range-class.md) , jeśli określona pozycja jest większa niż rozmiar bitset.

#### <a name="example"></a>Przykład

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a>zbiór

Ustawia wszystkie bity w bitset do 1 lub ustawia bit w określonym położeniu na 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja bitu w bitset, który ma być ustawiony na przypisaną wartość.

*val*\
Wartość, która ma zostać przypisana do bitu na określonej pozycji.

#### <a name="return-value"></a>Wartość zwrócona

Kopia elementu bitset, dla którego wywołano funkcję członkowską.

#### <a name="remarks"></a>Uwagi

Druga funkcja członkowska zgłasza wyjątek [out_of_range](../standard-library/out-of-range-class.md) , jeśli określona pozycja jest większa niż rozmiar bitset.

#### <a name="example"></a>Przykład

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a>zmienia

Zwraca liczbę bitów w obiekcie bitset.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Wartość zwrócona

Liczba bitów, *n*, w bitset\<N >.

#### <a name="example"></a>Przykład

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a>badan

Testuje, czy bit na określonej pozycji w bitset jest ustawiony na 1.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja bitu w bitset, który ma być testowany jako wartość.

#### <a name="return-value"></a>Wartość zwrócona

**true** , jeśli bit określony przez pozycję argumentu jest ustawiony na 1; w przeciwnym razie **false**.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska zgłasza [out_of_range](../standard-library/out-of-range-class.md)

### <a name="to_string"></a>to_string

Konwertuje obiekt bitset na reprezentację ciągu.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt String klasy `basic_string`, gdzie każdy bit ustawiony w bitset ma odpowiadający znak 1 i znak 0, jeśli bit jest nieustawiony.

#### <a name="example"></a>Przykład

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a>to_ullong

Zwraca **bez znaku** wartość Long Long, która zawiera te same bity ustawione jako zawartość obiektu bitset.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Wartość zwracana

Zwraca sumę wartości bitowych, które znajdują się w sekwencji bitowej jako **unsigned long long**. Ta **bezlong długa wartość** spowoduje ponowne utworzenie tego samego zestawu bitów, jeśli jest używany do inicjowania bitset.

#### <a name="exceptions"></a>Wyjątki

Zgłasza obiekt [overflow_error](overflow-error-class.md) , jeśli dowolny bit w sekwencji bitowej ma wartość bitową, która nie może być reprezentowana jako wartość typu **unsigned long long**.

#### <a name="remarks"></a>Uwagi

Zwraca sumę wartości bitowych, które znajdują się w sekwencji bitowej jako **unsigned long long**.

### <a name="to_ulong"></a>to_ulong

Konwertuje obiekt bitset na liczbę całkowitą, która spowodowałaby generowanie sekwencji bitów zawartych w przypadku użycia do zainicjowania bitset.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która spowodowałaby generowanie bitów w bitset, jeśli zostanie użyta podczas inicjowania bitset.

#### <a name="remarks"></a>Uwagi

Zastosowanie funkcji członkowskiej zwróci liczbę całkowitą, która ma taką samą sekwencję 1 i 0 cyfr, jak znaleziono w sekwencji bitów zawartej w bitset.

Funkcja członkowska zgłasza obiekt [overflow_error](overflow-error-class.md) , jeśli dowolny bit w sekwencji bitowej ma wartość bitową, która nie może być reprezentowana jako wartość typu **unsigned long**.

#### <a name="example"></a>Przykład

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
