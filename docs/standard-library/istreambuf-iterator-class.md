---
title: istreambuf_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 80bca2160f2e60938e9d0c85557b11a273c23264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363059"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator — Klasa

Szablon klasy istreambuf_iterator opisuje obiekt iteratora wejściowego, który wyodrębnia elementy znaków z buforu strumienia wejściowego, do którego uzyskuje dostęp za pośrednictwem obiektu, który przechowuje, wskaźnika typu `basic_streambuf` \< do **CharType**, **Cechy**>.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ, który reprezentuje typ znaków dla istreambuf_iterator.

*Cechy*\
Typ, który reprezentuje typ znaków dla istreambuf_iterator. Ten argument jest opcjonalny, `char_traits` \< a wartością domyślną jest *CharType>.*

## <a name="remarks"></a>Uwagi

Klasa istreambuf_iterator musi spełniać wymagania dla iteratora danych wejściowych.

Po skonstruowaniu lub inkrementacji obiektu klasy istreambuf_iterator ze wskaźnikiem przechowywanym bez wartości null obiekt skutecznie próbuje wyodrębnić i przechowywać obiekt typu *CharType* ze skojarzonego strumienia wejściowego. Wyodrębnienie może jednak zostać opóźnione, dopóki obiekt jest rzeczywiście wyłuskiwany lub kopiowany. Jeśli wyodrębnienie się nie uda, obiekt skutecznie zastępuje przechowywany wskaźnik wskaźnikiem pustym, tworząc wskaźnik końca sekwencji.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Konstruuje `istreambuf_iterator` zainicjowany, aby odczytać znaki ze strumienia wejściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ, który zawiera typ znaku `ostreambuf_iterator`.|
|[Int_type](#int_type)|Typ, który zawiera typ liczby `istreambuf_iterator`całkowitej dla pliku .|
|[istream_type](#istream_type)|Typ, który zapewnia typ strumienia `istream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, który zapewnia typ strumienia `istreambuf_iterator`.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Typ, który zawiera typ cech charakteru `istream_iterator`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Równe](#equal)|Sprawdza pod kątem równości dwóch iteratorów bufora strumienia wejściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*](#op_star)|Operator dereferencji zwraca następny znak w strumieniu.|
|[operator++](#op_add_add)|Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.|
|[operator->](#op_arrow)|Zwraca wartość elementu członkowskiego, jeśli istnieje.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator::char_type

Typ, który zawiera typ znaku `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *CharType*.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator::równe

Testy równoważności między dwoma iteratorami buforu strumienia wejściowego.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Iterator, dla którego należy sprawdzić równość.

### <a name="return-value"></a>Wartość zwracana

**true,** `istreambuf_iterator`jeśli oba s są iteratory końca strumienia lub jeśli nie jest iteratorem końca strumienia; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zakres jest zdefiniowany `istreambuf_iterator` przez do bieżącej pozycji i iteratora końca strumienia, ale ponieważ wszystkie iteratory `equal` nienajmowe strumienia są równoważne `istreambuf_iterator`w ramach funkcji elementu członkowskiego, nie jest możliwe zdefiniowanie żadnych podzakresów przy użyciu s. I `==` `!=` operatorów mają taką samą semantykę.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator::int_type

Typ, który zawiera typ liczby `istreambuf_iterator`całkowitej dla pliku .

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `Traits::int_type`.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator::istream_type

Typ, który zapewnia typ strumienia `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basic_istream` \< **CharType**, **Cechy**>.

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator,](#istreambuf_iterator) aby zapoznać się z `istream_type`przykładem deklarowania i używania pliku .

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator::istreambuf_iterator

Tworzy istreambuf_iterator, który jest inicjowany do odczytu znaków ze strumienia wejściowego.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Bufor strumienia wejściowego, `istreambuf_iterator` do którego jest dołączony.

*_Istr*\
Strumień wejściowy, `istreambuf_iterator` do którego jest dołączony.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje wskaźnik buforu strumienia wejściowego za pomocą *strbuf*. Drugi konstruktor inicjuje wskaźnik buforu strumienia wejściowego z *_Istr*. `rdbuf`, a następnie ostatecznie próbuje wyodrębnić i `CharType`zapisać obiekt typu .

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator::operator*

Operator dereferencji zwraca następny znak w strumieniu.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Następny znak w strumieniu.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator::operator++

Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie `istreambuf_iterator` lub odwołanie `istreambuf_iterator`do pliku .

### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i przechowywać obiekt typu `CharType` z skojarzonego strumienia wejściowego. Drugi operator tworzy kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator::operator-&gt;

Zwraca wartość elementu członkowskiego, jeśli istnieje.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca ** & \* \*to**.

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator::streambuf_type

Typ, który zapewnia typ strumienia istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basic_streambuf` \< **CharType**, **Cechy**>.

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator,](#istreambuf_iterator) aby zapoznać się z `istreambuf_type`przykładem deklarowania i używania pliku .

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator::traits_type

Typ, który zawiera typ cech charakteru `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Cechy*.

### <a name="example"></a>Przykład

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>Zobacz też

[Struktura iteratora](../standard-library/iterator-struct.md)\
[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
