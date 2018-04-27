---
title: istreambuf_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
dev_langs:
- C++
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf6e5e68d06cb17a51e37c4051fea6bd11eccede
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istreambufiterator-class"></a>istreambuf_iterator — Klasa

Istreambuf_iterator — klasa szablonu opisuje wyodrębniające elementy znak z bufora strumienia wejściowego, który uzyskuje dostęp do za pośrednictwem obiektu przechowuje, typ wskaźnika do obiektu wejściowego iteratora `basic_streambuf` \< **CharType** , **Cech**>.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parametry

`CharType` Typ reprezentujący typ znaków istreambuf_iterator —.

`Traits` Typ reprezentujący typ znaków istreambuf_iterator —. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType >.*

## <a name="remarks"></a>Uwagi

Klasa istreambuf_iterator musi spełniać wymagania dla iteratora danych wejściowych.

Po konstruowania lub zwiększanie obiektu istreambuf_iterator — klasa za pomocą wskaźnika składowaną innych niż null, obiekt skutecznie próbuje wyodrębnić i zapisania obiektu typu **CharType** ze strumienia wejściowego skojarzone. Wyodrębnienie może jednak zostać opóźnione, dopóki obiekt jest rzeczywiście wyłuskiwany lub kopiowany. Jeśli wyodrębnienie się nie uda, obiekt skutecznie zastępuje przechowywany wskaźnik wskaźnikiem pustym, tworząc wskaźnik końca sekwencji.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Konstruuje `istreambuf_iterator` który jest ustawiana na odczytywanie znaków ze strumienia wejściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zawiera znak typu `ostreambuf_iterator`.|
|[int_type](#int_type)|Typ, który zapewnia całkowitą dla `istreambuf_iterator`.|
|[istream_type](#istream_type)|Typ, który udostępnia dla typu strumienia `istream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, który udostępnia dla typu strumienia `istreambuf_iterator`.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Typ, który zawiera typ cech znaków `istream_iterator`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[equal](#equal)|Sprawdza pod kątem równości dwóch iteratorów bufora strumienia wejściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator dereferencji zwraca następny znak w strumieniu.|
|[operator++](#op_add_add)|Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.|
|[operator ->](#op_arrow)|Zwraca wartość elementu członkowskiego, jeśli istnieje.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="char_type"></a>  istreambuf_iterator::char_type

Typ, który zawiera znak typu `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

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

## <a name="equal"></a>  istreambuf_iterator::EQUAL

Testy do pełnienia roli równoważnika między dwoma Iteratory buforu strumienia wejściowego.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parametry

`right` Iterator, dla którego ma być sprawdzany pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obie `istreambuf_iterator`s są Iteratory zakończenia z strumienia lub jeśli nie jest iteratora zakończenia elementu strumienia; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zakres jest definiowana za pomocą `istreambuf_iterator` do bieżącego położenia i iteratora zakończenia z strumienia, ale od wszystkich innych niż koniec strumienia Iteratory są równoważne w obszarze **równy** funkcja członkowska nie jest możliwe do definiowania żadnych podzakresy przy użyciu `istreambuf_iterator`s. `==` i `!=` operatorzy mają tej samej semantyki.

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

## <a name="int_type"></a>  istreambuf_iterator::int_type

Typ, który zapewnia całkowitą dla `istreambuf_iterator`.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem **Traits::int_type**.

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
\* Output:
The inttype1 = 100.
*\
```

## <a name="istream_type"></a>  istreambuf_iterator::istream_type

Typ, który udostępnia dla typu strumienia `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basic_istream` \< **CharType**, **cech**>.

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator —](#istreambuf_iterator) przykład sposobu deklarowanie i użycie `istream_type`.

## <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator

Tworzy istreambuf_iterator —, która jest ustawiana na odczytywanie znaków ze strumienia wejściowego.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parametry

`strbuf` Bufor strumienia wejściowego, do którego `istreambuf_iterator` jest dołączony.

`_Istr` Strumień wejściowy, do którego `istreambuf_iterator` jest dołączony.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnika buforu strumienia wejściowego z `strbuf`. Drugi Konstruktor inicjuje wskaźnika buforu strumienia wejściowego z `_Istr`. `rdbuf`i po pewnym czasie próbuje wyodrębnić i przechowywania obiektów typu **CharType**.

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

## <a name="op_star"></a>  istreambuf_iterator::operator *

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

## <a name="op_add_add"></a>  istreambuf_iterator::operator ++

Zwraca następny znak ze strumienia wejściowego lub kopiuje obiekt przed jego inkrementacją i zwraca kopię.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

`istreambuf_iterator` Lub odwołanie do `istreambuf_iterator`.

### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i zapisania obiektu typu **CharType** ze strumienia wejściowego skojarzone. Drugi operator tworzy kopię obiektu, zwiększa obiektu, a następnie zwraca kopii.

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

## <a name="op_arrow"></a>  istreambuf_iterator::operator-&gt;

Zwraca wartość elementu członkowskiego, jeśli istnieje.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Operator zwraca  **& \* \*to**.

## <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type

Typ, który udostępnia dla typu strumienia istreambuf_iterator —.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basic_streambuf` \< **CharType**, **cech**>.

### <a name="example"></a>Przykład

Zobacz [istreambuf_iterator —](#istreambuf_iterator) przykład sposobu deklarowanie i użycie **istreambuf_type**.

## <a name="traits_type"></a>  istreambuf_iterator::traits_type

Typ, który zawiera typ cech znaków `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **cech**.

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

[iterator, struktura](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
