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
ms.openlocfilehash: f580e56efe1db42e464deedfa66da861ff897bcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380256"
---
# <a name="bitset-class"></a>bitset — Klasa

Opisuje typ obiektu, który przechowuje sekwencji składającej się z stałą liczbą bitów, które zapewniają zwarty sposób zachowania flagi dla zestawu elementów lub warunki. Bitset — klasa obsługuje operacje na obiektach bitset — typ, które zawierają kolekcję usługi bits i udostępnienia czasie stałym każdy bit.

## <a name="syntax"></a>Składnia

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parametry

*N*<br/>
Określa liczbę bitów w obiekcie bitset — z liczbą całkowitą różną od zera typu `size_t` musi być znane w czasie kompilacji.

## <a name="remarks"></a>Uwagi

W odróżnieniu od podobny [wektor\<bool > klasa](../standard-library/vector-bool-class.md), bitset — klasa nie ma iteratorów, a nie jest kontenerem standardowej biblioteki języka C++. Również różni się od wektor\<bool > przez ich niektóre określonego rozmiaru, które są ustalane w czasie kompilacji, zgodnie z rozmiaru określonego przez parametr szablonu *N* podczas **bitset —\<N\>**  jest zadeklarowana.

Bit jest ustawiona, jeśli jego wartość wynosi 1 i zresetowanie, jeśli jego wartość wynosi 0. Przerzuć lub odwracanie bit jest zmień jej wartość z zakresu od 1 na 0 lub od 0 do 1. *N* bitów zestawu bitów są indeksowane według wartości liczby całkowitej z zakresu od 0 do *N* -1, gdzie 0 indeksuje pierwszy pozycja bitu i *N* - 1 końcowe bit pozycji.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[bitset —](#bitset)|Tworzy obiekt klasy `bitset\<N>` i inicjuje bitów na zero, niektóre określonej wartości lub wartości uzyskane z znaków w ciągu.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[element_type](#element_type)|Typ, który jest synonimem dla typu danych **bool** i może służyć do odwołania elementu bitów `bitset`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Wszystkie](#all)|Sprawdza wszystkie bity, w tym `bitset` do ustalenia, czy są gotowi do **true**.|
|[Wszystkie](#any)|Funkcja elementu członkowskiego sprawdza, czy każdego bitu w sekwencji jest ustawiona na 1.|
|[Liczba](#count)|Element członkowski funkcji zwraca liczbę bitów w bitową sekwencję.|
|[flip](#flip)|Odwraca wszystkie bity w wartości `bitset` lub odwraca pojedynczy bit na określonej pozycji.|
|[Brak](#none)|Sprawdza, czy ustawiono nie bit na 1 `bitset` obiektu.|
|[Resetuj](#reset)|Resetuje wszystkie bity w `bitset` na 0 lub resetuje chwilę na określonej pozycji na 0.|
|[set](#set)|Ustawia wszystkie bity w `bitset` 1 lub ustawia bit na określonej pozycji 1.|
|[Rozmiar](#size)|Zwraca liczbę bitów w `bitset` obiektu.|
|[Test](#test)|Testy czy bit na określonej pozycji w `bitset` jest ustawiona na 1.|
|[to_string](#to_string)|Konwertuje `bitset` obiektu na reprezentację ciągu.|
|[to_ullong](#to_ullong)|Zwraca sumę wartości bitowe w `bitset` jako **unsigned long long**.|
|[to_ulong](#to_ulong)|Konwertuje `bitset` obiekt **unsigned long** , wygenerowanie sekwencji bitów zawartych, jeśli jest używane do zainicjowania `bitset`.|

### <a name="member-classes"></a>Element członkowski klasy

|Element członkowski klasy|Opis|
|-|-|
|[Odwołanie](#reference)|Klasy serwera proxy, który zawiera odwołania do bitów zawartych w `bitset` używany do uzyskiwania dostępu i manipulowania pojedynczych bitów jako klasa pomocnicza do `operator[]` klasy `bitset`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Testuje, obiekt docelowy `bitset` pod kątem nierówności z określonym `bitset`.|
|[operator&=](#op_and_eq)|Wykonuje bitową kombinację bitsets z logicznym `AND` operacji.|
|[Operator <<](#op_lshift)|Wykonuje przesunięcie bitów w `bitset` określoną liczbę pozycji po lewej stronie i zwraca wynik do nowego `bitset`.|
|[Operator << =](#op_lshift_eq)|Wykonuje przesunięcie bitów w `bitset` określoną liczbę pozycji po lewej stronie i zwraca wynik na docelową `bitset`.|
|[operator==](#op_eq_eq)|Testuje, obiekt docelowy `bitset` pod kątem równości z określonym `bitset`.|
|[operator>>](#op_rshift)|Wykonuje przesunięcie bitów w `bitset` określoną liczbę pozycji po prawej stronie i zwraca wynik do nowego `bitset`.|
|[operator>>=](#op_rshift_eq)|Wykonuje przesunięcie bitów w `bitset` określoną liczbę pozycji po prawej stronie i zwraca wynik na docelową `bitset`.|
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do bitu na określonej pozycji w `bitset` Jeśli `bitset` jest modyfikowalny; w przeciwnym razie zwraca wartość bitu na tej pozycji.|
|[operator^=](#op_xor_eq)|Wykonuje bitową kombinację bitsets z jedynego `OR` operacji.|
|[operator&#124;=](#op_or_eq)|Wykonuje bitową kombinację bitsets z włącznie `OR` operacji.|
|[operator~](#op_not)|Odwraca wszystkie bity w elemencie docelowym `bitset` i zwraca wynik.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<bitset — >

**Namespace:** standardowe

## <a name="all"></a>  bitset::all

Sprawdza wszystkie bity, w tym bitset — Aby ustalić, czy są ustawione na wartość true.

```cpp
bool all() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli spełnione są wszystkie bity w tym zestawie. Zwraca **false** Jeśli co najmniej jeden usługi bits mają wartość false.

## <a name="any"></a>  bitset::any

Sprawdza, czy każdego bitu w sekwencji jest ustawiona na 1.

```cpp
bool any() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli każdego bitu, bitset — jest ustawiona na 1; **false** Jeśli wszystkie bity są równe 0.

### <a name="example"></a>Przykład

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

## <a name="bitset"></a>  bitset::bitset

Tworzy obiekt klasy `bitset\<N>` i inicjuje bity na wartość 0, lub na określoną wartość lub wartości uzyskane z znaków w ciągu.

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

### <a name="parameters"></a>Parametry

*Val*<br/>
Bez znaku liczby całkowitej, którego reprezentacja base dwóch służy do inicjowania usługi bits w bitset — są zbudowane.

*str*<br/>
Ciąg zer i używane do zainicjowania wartości bitowe bitset —.

*_CStr*<br/>
Ciąg stylu C zer i używane do zainicjowania wartości bitowe bitset —.

*_Pos*<br/>
Pozycja znaku w ciągu, licząc od lewej do prawej i rozpoczynającą się od zera, używany do inicjowania pierwszego bitu bitset —.

*Liczba*<br/>
Liczba znaków w ciągu, który służy do zapewnienia wartości początkowe usługi bits w bitset —.

*_Zero*<br/>
Znak, który jest używany do reprezentowania zero. Wartość domyślna to "0".

*_Co*<br/>
Znak, który jest używany do reprezentowania jednego. Wartość domyślna to "1".

### <a name="remarks"></a>Uwagi

Trzy konstruktory może służyć do konstruowania obects klasy `bitset\<N>`:

- Pierwszy Konstruktor akceptuje żadnych parametrów, konstruuje obiekt klasy `bitset\<N>` i inicjuje wszystkie bity N na wartość domyślną równą zero.

- Drugi Konstruktor konstruuje obiekt klasy `bitset\<N>` i inicjuje usługi bits przy użyciu pojedynczej precyzji **unsigned long long** parametru.

- Trzeci Konstruktor konstruuje obiekt klasy `bitset\<N>`, inicjowanie N bits do wartości, które odnoszą się do znaków w ciągu znaków stylu c zer i z nich. Wywołanie konstruktora bez rzutowania ciąg do typu string: `bitset<5> b5("01011");`

Istnieją dwa szablony konstruktora, pod warunkiem:

- Pierwszy szablon Konstruktor konstruuje obiekt klasy `bitset\<N>` i inicjuje bitów ze znaków w ciągu zer i z nich. Jeśli dowolne znaki ciągu są inne niż 0 lub 1, Konstruktor wyrzuca obiekt klasy [nieprawidłowy argument](../standard-library/invalid-argument-class.md). Jeśli określona pozycja (*_Pos*) wykracza poza długość ciągu, a następnie Konstruktor wyrzuca obiekt klasy [out_of_range —](../standard-library/out-of-range-class.md). Konstruktor określa tylko te usługi bits w położeniu *"j"* w bitset —, dla której znak w ciągu w położeniu `_Pos + j` 1. Domyślnie *_Pos* wynosi 0.

- Drugi Konstruktor, który jest podobny do pierwszego, ale zawiera dodatkowy parametr (*liczba*) używany do określenia liczby bitów, aby zainicjować. Ma również dwa parametry opcjonalne, *_Zero* i *_Jedna*, które wskazują, jakie znak w *str* ma być interpretowany jako oznaczenie 0 bit i 1 bit odpowiednio.

### <a name="example"></a>Przykład

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

## <a name="count"></a>  bitset::Count

Zwraca liczbę bitów w bitową sekwencję.

```cpp
size_t count() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba bitów w bitową sekwencję.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie bitset::count funkcja elementu członkowskiego.

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

## <a name="element_type"></a>  bitset::ELEMENT_TYPE

Typ, który jest synonimem dla typu danych **bool** i może służyć do odwołania elementu bitów zestawu bitów.

```cpp
typedef bool element_type;
```

### <a name="example"></a>Przykład

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

## <a name="flip"></a>  bitset::Flip

Odwraca wartość wszystkie bity w zestawu bitów lub odwraca pojedynczy bit na określonej pozycji.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycja bitu, którego wartość ma być zmieniany.

### <a name="return-value"></a>Wartość zwracana

Kopia zmodyfikowane bitset —, dla którego została wywołana funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Funkcja drugiego członka zgłasza [out_of_range —](../standard-library/out-of-range-class.md) wyjątek, jeśli określona jako parametr pozycja jest większa niż rozmiar *N* z **bitset —\<**  *N* **>** którego bitowa została odwrócona.

### <a name="example"></a>Przykład

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

## <a name="none"></a>  bitset::none

Sprawdza, czy bit nie została ustawiona na 1 w obiekcie bitset —.

```cpp
bool none() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli nie bitu bitset — została ustawiona na 1; **false** Jeśli co najmniej jeden bit została ustawiona na 1.

### <a name="example"></a>Przykład

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

## <a name="op_neq"></a>  bitset::operator! =

Testy zestawu docelowego bitów pod kątem nierówności z określonego zestawu bitów.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Bitset — jest porównywana bitset — docelowego pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bitsets różnią się; **false** jeśli są takie same.

### <a name="remarks"></a>Uwagi

Bitsets musi być taki sam rozmiar, ma zostać przetestowana pod kątem nierówności przy użyciu funkcji operatora składowej.

### <a name="example"></a>Przykład

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

## <a name="op_and_eq"></a>  bitset::operator&amp;=

Wykonuje bitową kombinację bitsets z logicznym `AND` operacji.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Bitset — to być łączone bitowego z bitset — docelowy.

### <a name="return-value"></a>Wartość zwracana

Bitset — modyfikowanych docelowych, która wynika z operatora testu koniunkcji `AND` operację, podając bitset — określony jako parametr.

### <a name="remarks"></a>Uwagi

Dwa bity są połączone za `AND` operator zwrotny **true** Jeśli każdy bit ma wartość PRAWDA; w przeciwnym razie ich kombinacji zwraca **false**.

Bitsets musi być taki sam rozmiar, ma być wyłączny sumy bitowej połączona z `AND` operator przy użyciu funkcji operatora składowej.

### <a name="example"></a>Przykład

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

## <a name="op_lshift"></a> bitset::operator\<\<

Przesuwa bity w zestawu bitów w lewo określoną liczbę pozycji i zwraca wynik do nowego zestawu bitów.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Numer pozycji w lewo, że bity w bitset — są lekkie.

### <a name="return-value"></a>Wartość zwracana

Zmodyfikowane bitset — za pomocą usługi bits przesuwane w lewo, wymagana liczba stanowisk.

### <a name="remarks"></a>Uwagi

Funkcja operator elementu członkowskiego zwraca **bitset —**(  **\*to**) **<< = punktu sprzedaży,** gdzie [ <<= ](#op_lshift_eq) przenosi bity w zestawu bitów określoną liczbę pozycji po lewej stronie i zwraca wynik do docelowych bitset —.

### <a name="example"></a>Przykład

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

## <a name="op_lshift_eq"></a>  bitset::operator&lt;&lt;=

Przesuwa bity w zestawu bitów w lewo określoną liczbę pozycji i zwraca wynik do docelowych bitset —.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Numer pozycji w lewo, bity w bitset — są lekkie.

### <a name="return-value"></a>Wartość zwracana

Docelowe bitset — zmodyfikowany tak, że bity zostały przesunięte w lewo wymagana liczba stanowisk.

### <a name="remarks"></a>Uwagi

Jeśli element nie istnieje spowoduje przejście do pozycji, funkcja czyści na wartość 0.

### <a name="example"></a>Przykład

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

## <a name="op_eq_eq"></a>  bitset::operator ==

Testy zestawu docelowego bitów pod kątem równości z określonego zestawu bitów.

```cpp
bool operator==(const bitset\<N>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Bitset — jest porównywana bitset — docelowego pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bitsets są takie same; **false** są różne.

### <a name="remarks"></a>Uwagi

Bitsets musi być taki sam rozmiar, ma zostać przetestowana pod kątem równości, funkcji operatora składowej.

### <a name="example"></a>Przykład

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

## <a name="op_rshift"></a>  bitset::operator&gt;&gt;

Przesuwa bity w bitset — z prawej strony określoną liczbę pozycji i zwraca wynik do nowego zestawu bitów.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Liczba pozycji po prawej stronie, że bity w bitset — są lekkie.

### <a name="return-value"></a>Wartość zwracana

Nowe bitset —, gdy bity zostały przesunięte w prawo wymaganą liczbę pozycji względem docelowych bitset —.

### <a name="example"></a>Przykład

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

## <a name="op_rshift_eq"></a>  bitset::operator&gt;&gt;=

Przesuwa bity w bitset — z prawej strony określoną liczbę pozycji i zwraca wynik do docelowych bitset —.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Liczba pozycji po prawej stronie, że bity w bitset — są lekkie.

### <a name="return-value"></a>Wartość zwracana

Docelowe bitset — zmodyfikowany tak, że bity zostały przesunięte w prawo wymagana liczba stanowisk.

### <a name="remarks"></a>Uwagi

Jeśli element nie istnieje spowoduje przejście do pozycji, funkcja czyści na wartość 0.

### <a name="example"></a>Przykład

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

## <a name="op_at"></a>  bitset::operator]

Zwraca odwołanie do bitu na określonej pozycji w bitset — w przypadku modyfikowalnych; bitset — w przeciwnym razie zwraca wartość bitu na tej pozycji.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycja lokalizowanie bit w bitset —.

### <a name="remarks"></a>Uwagi

Podczas definiowania [ \_ITERATORA\_debugowania\_poziom](../standard-library/iterator-debug-level.md) jako 1 lub 2 w kompilacji, wystąpi błąd czasu wykonywania w plik wykonywalny przy próbie uzyskania dostępu do elementu poza granicami bitset —. Aby uzyskać więcej informacji dotyczących, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

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

## <a name="op_xor_eq"></a>  bitset::operator ^ =

Wykonuje bitową kombinację bitsets z jedynego `OR` operacji.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Bitset — to być łączone bitowego z bitset — docelowy.

### <a name="return-value"></a>Wartość zwracana

Bitset — modyfikowanych docelowych, które powstały na skutek wyłączny sumy bitowej `OR` operację, podając bitset — określony jako parametr.

### <a name="remarks"></a>Uwagi

Dwa bity połączone przez jedynego **lub** operator zwrotny **true** Jeśli co najmniej jeden, ale nie obu bitów jest **true**; w przeciwnym razie ich kombinacji zwraca **false**.

Bitsets musi być taki sam rozmiar, ma być wyłączny sumy bitowej połączona z jedynego `OR` operator przy użyciu funkcji operatora składowej.

### <a name="example"></a>Przykład

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

## <a name="op_or_eq"></a>  bitset::operator&#124;=

Wykonuje bitową kombinację bitsets z włącznie `OR` operacji.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Bitset — to być łączone bitowego z bitset — docelowy.

### <a name="return-value"></a>Wartość zwracana

Bitset — modyfikowanych docelowych, która wynika z operatora testu koniunkcji włącznie `OR` operację, podając bitset — określony jako parametr.

### <a name="remarks"></a>Uwagi

Dwa bity w połączeniu, włącznie `OR` operator zwrotny **true** Jeśli co najmniej jeden z bitów jest **true**; Jeśli oba bity są **false**, zwraca ich kombinacji **false**.

Bitsets musi być taki sam rozmiar, które można połączyć alternatywy bitowej przy użyciu włącznie `OR` operator przy użyciu funkcji operatora składowej.

### <a name="example"></a>Przykład

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

## <a name="op_not"></a>  bitset::operator ~

Odwraca wszystkie bity w docelowego zestawu bitów i zwraca wynik.

```cpp
bitset\<N> operator~() const;
```

### <a name="return-value"></a>Wartość zwracana

Bitset — za pomocą jego bitów odwrócony w odniesieniu do docelowych bitset —.

### <a name="example"></a>Przykład

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

## <a name="reference"></a>  bitset::Reference

Klasa serwera proxy, która zawiera odwołania do bitów zawartych w bitset —, używanego do uzyskiwania dostępu i manipulowania pojedynczych bitów jako klasa pomocnicza do `operator[]` z bitset — klasa.

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

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość obiektu typu **bool** przypisuje się nieco w zestawu bitów.

*_Bitref*<br/>
Odwołanie do formularza *x [i]* do bitu w położeniu *i* w bitset — *x*.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bitu w bitset — określone przez pozycja argumentu dla pierwszego, drugiego i piąty funkcje składowe odwołań do klas i **true** lub **false**w celu odzwierciedlenia wartości zmodyfikowane bit w bitset — funkcji elementu członkowskiego trzecia i czwarta odwołania do klasy.

### <a name="remarks"></a>Uwagi

Klasa `reference` istnieje tylko jako klasa pomocnicza do bitset — `operator[]`. Klasa składowej opisuje obiekt, który mogą uzyskiwać dostęp do poszczególnych bitowe, w ramach zestawu bitów. Pozwól *b* być obiektem typu **bool**, *x* i *y* obiektów typu **bitset —\<**  *N* **>**, i *i* i *"j"* prawidłowe położenie takiego obiektu. Notacja *x [i]* odwołuje się do bitu w położeniu *i* w bitset — *x*. Funkcje elementów członkowskich klasy `reference` zapewniają kolejno następujące operacje:

|Operacja|Definicja|
|---------------|----------------|
|*x*[*i*] = *b*|Magazyny **bool** wartość *b* pozycja bit *i* w bitset — *x*.|
|*x*[*i*] = *y*[*j*]|Przechowuje wartość bitu *y*[ *"j"*] pozycja bit *i* w bitset — *x*.|
|*b* = ~ *x*[*i*]|Przechowuje wartość odwrócony bitu *x*[ *i*] w **bool** *b*.|
|*b* = *x*[*i*]|Przechowuje wartość bitu *x*[ *i*] w **bool** *b*.|
|*x*[*i*]. `flip`( )|Przechowuje wartość odwrócony bitu *x*[ *i*] w pozycji bitu *i* w *x*.|

### <a name="example"></a>Przykład

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

## <a name="reset"></a>  bitset::reset

Resetuje wszystkie bity w zestawu bitów na 0 lub resetuje chwilę na określonej pozycji na 0.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycja bitu bitset — aby zresetowane do wartości 0.

### <a name="return-value"></a>Wartość zwracana

Kopia bitset —, dla którego została wywołana funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Funkcja drugiego członka zgłasza [out_of_range —](../standard-library/out-of-range-class.md) wyjątek, jeśli określona pozycja jest większa niż rozmiar bitset —.

### <a name="example"></a>Przykład

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

## <a name="set"></a>  bitset::set

Ustawia bit wszystkie bity w zestawu bitów 1 lub zestawy na określonej pozycji 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycja bitu w bitset — należy ustawić przypisanej wartości.

*Val*<br/>
Wartość do przypisania do bitu na określonej pozycji.

### <a name="return-value"></a>Wartość zwracana

Kopia bitset —, dla którego została wywołana funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Funkcja drugiego członka zgłasza [out_of_range —](../standard-library/out-of-range-class.md) wyjątek, jeśli określona pozycja jest większa niż rozmiar bitset —.

### <a name="example"></a>Przykład

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

## <a name="size"></a>  bitset::size

Zwraca liczbę bitów w obiekcie bitset —.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba bitów, *N*, w bitset —\<N >.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie bitset::size funkcja elementu członkowskiego.

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

## <a name="test"></a>  bitset::test

Sprawdza, czy bit na określonej pozycji w zestawu bitów jest ustawiona na 1.

```cpp
bool test(size_t _Pos) const;
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycja bitu bitset — do przetestowania jako jej wartość.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli bitu określonego przez argument pozycji jest ustawiona na 1; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zgłasza [out_of_range —](../standard-library/out-of-range-class.md)

## <a name="to_string"></a> bitset::to_string

Konwertuje ciąg reprezentujący obiekt bitset —.

```
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt ciągu klasy `basic_string`, gdzie każdego bitu w bitset — ma odpowiedniego znaku 1 i znaku 0, jeśli to nie ustawiono bitu.

### <a name="example"></a>Przykład

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

## <a name="to_ullong"></a> bitset::to_ullong

Zwraca **unsigned long long** wartość, która zawiera ten sam bity Ustaw jako zawartość obiektu bitset —.

```
unsigned long long to_ullong() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca sumę wartości bitowe, które znajdują się w bitową sekwencję jako **unsigned long long**. To **unsigned long long** wartość będzie ponownie utworzyć bitów zestawu w tym samym, jeśli jest używany do inicjowania zestawu bitów.

### <a name="exceptions"></a>Wyjątki

Zgłasza [overflow_error —](overflow-error-class.md) obiektu, jeśli każdego bitu, bitową sekwencję nieco ma wartość, która nie może być przedstawiony jako wartość typu **unsigned long long**.

### <a name="remarks"></a>Uwagi

Zwraca sumę wartości bitowe, które znajdują się w bitową sekwencję jako **unsigned long long**.

## <a name="to_ulong"></a> bitset::to_ulong

Konwertuje obiekt bitset — liczba całkowita, która powoduje wygenerowanie sekwencji znajdujące się użyć do zainicjowania bitset — usługi bits.

```
unsigned long to_ulong( ) const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która wygeneruje bity w bitset — wykorzystywane w inicjowaniu bitset —.

### <a name="remarks"></a>Uwagi

Stosowanie funkcji elementu członkowskiego zwróci liczbę całkowitą, która ma taką samą sekwencję cyfr 1 i 0, ponieważ znajduje się w sekwencji bitów zawartych w bitset —.

Funkcja elementu członkowskiego zgłasza [overflow_error —](overflow-error-class.md) obiektu, jeśli każdego bitu, bitową sekwencję nieco ma wartość, która nie może być przedstawiony jako wartość typu **unsigned long**.

### <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz także

[\<bitset — >](bitset.md)<br/>
[bitset — operatory](bitset-operators.md)<br/>
