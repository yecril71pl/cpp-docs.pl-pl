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
ms.openlocfilehash: b76e327c46a180c1e7ae7287ee9fe49573f3a7a6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217704"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator — Klasa

Szablon klasy istreambuf_iterator opisuje obiekt iteratora wejściowego, który wyodrębnia elementy znaków z bufora strumienia wejściowego, do którego uzyskuje dostęp przez obiekt, który przechowuje, typu wskaźnika do `basic_streambuf` \< **CharType**, **Traits**> .

## <a name="syntax"></a>Składnia

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ, który reprezentuje typ znaków dla istreambuf_iterator.

*Cech*\
Typ, który reprezentuje typ znaków dla istreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType> . *

## <a name="remarks"></a>Uwagi

Klasa istreambuf_iterator musi spełniać wymagania dla iteratora danych wejściowych.

Po skonstruowaniu lub zwiększeniu obiektu klasy istreambuf_iterator z niezerowym wskaźnikiem przechowywanym obiekt skutecznie próbuje wyodrębnić i przechowywać obiekt typu *CharType* ze skojarzonego strumienia wejściowego. Wyodrębnienie może jednak zostać opóźnione, dopóki obiekt jest rzeczywiście wyłuskiwany lub kopiowany. Jeśli wyodrębnienie się nie uda, obiekt skutecznie zastępuje przechowywany wskaźnik wskaźnikiem pustym, tworząc wskaźnik końca sekwencji.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Tworzy obiekt `istreambuf_iterator` , który jest inicjowany do odczytu znaków ze strumienia wejściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zapewnia typ znaku `ostreambuf_iterator` .|
|[int_type](#int_type)|Typ, który dostarcza typ Integer dla elementu `istreambuf_iterator` .|
|[istream_type](#istream_type)|Typ, który zapewnia typ strumienia `istream_iterator` .|
|[streambuf_type](#streambuf_type)|Typ, który zapewnia typ strumienia `istreambuf_iterator` .|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Typ, który zapewnia dla typu cechy znakowe `istream_iterator` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[większy](#equal)|Sprawdza pod kątem równości dwóch iteratorów bufora strumienia wejściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji zwraca następny znak w strumieniu.|
|[operator + +](#op_add_add)|Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.|
|[operator — >](#op_arrow)|Zwraca wartość elementu członkowskiego, jeśli istnieje.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<iterator>

**Przestrzeń nazw:** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator:: char_type

Typ, który zapewnia typ znaku `ostreambuf_iterator` .

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *CharType*.

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

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator:: EQUAL

Testuje równoważność między dwoma iteratorami bufora strumienia wejściowego.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Iterator, dla którego ma zostać wyszukana równość.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli oba `istreambuf_iterator` s są iteratorami końca strumienia lub jeśli nie są iteratorami końca strumienia; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zakres jest definiowany przez `istreambuf_iterator` do bieżącego położenia i iteratora końca strumienia, ale ponieważ wszystkie Iteratory strumienia niekończącego są równoważne pod `equal` funkcją składową, nie można definiować żadnych zakresów podrzędnych przy użyciu `istreambuf_iterator` . `==`Operatory i `!=` mają tę samą semantykę.

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

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator:: int_type

Typ, który dostarcza typ Integer dla elementu `istreambuf_iterator` .

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `Traits::int_type` .

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

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator:: istream_type

Typ, który zapewnia typ strumienia `istreambuf_iterator` .

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basic_istream` \< **CharType**, **Traits**> .

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator](#istreambuf_iterator) , aby zapoznać się z przykładem sposobu deklarowania i używania `istream_type` .

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator:: istreambuf_iterator

Konstruuje istreambuf_iterator, który jest inicjowany do odczytu znaków ze strumienia wejściowego.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Bufor strumienia wejściowego, do którego `istreambuf_iterator` jest dołączany.

*_Istr*\
Strumień wejściowy, do którego `istreambuf_iterator` jest dołączany.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnik wejściowego buforu strumienia z *strbuf*. Drugi Konstruktor inicjuje wskaźnik bufora strumienia wejściowego z *_Istr*. `rdbuf`, a następnie ostatecznie próbuje wyodrębnić i przechowywać obiekt typu `CharType` .

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator:: operator *

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator:: operator + +

Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

`istreambuf_iterator`Lub odwołanie do `istreambuf_iterator` .

### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i przechowywać obiekt typu `CharType` ze skojarzonego strumienia wejściowego. Drugi operator wykonuje kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

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

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator:: operator-&gt;

Zwraca wartość elementu członkowskiego, jeśli istnieje.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca ** & \* \* tę**wartość.

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator:: streambuf_type

Typ, który zapewnia typ strumienia istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basic_streambuf` \< **CharType**, **Traits**> .

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator](#istreambuf_iterator) , aby zapoznać się z przykładem sposobu deklarowania i używania `istreambuf_type` .

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator:: traits_type

Typ, który zapewnia dla typu cechy znakowe `istream_iterator` .

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla *cech*parametrów szablonu.

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

## <a name="see-also"></a>Zobacz także

[Iterator — struktura](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
