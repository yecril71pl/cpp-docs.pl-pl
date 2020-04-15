---
title: Klasa ostreambuf_iterator
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: 8e9fa10888b511ad2a500f64faf610dc7dd5ba03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373562"
---
# <a name="ostreambuf_iterator-class"></a>Klasa ostreambuf_iterator

Szablon klasy ostreambuf_iterator opisuje obiekt iteratora wyjściowego, który zapisuje kolejne elementy znaków na strumieniu wyjściowym za pomocą operatora wyodrębniania **>>**. S `ostreambuf_iterator`różnią się od tych [z ostream_iterator Class](../standard-library/ostream-iterator-class.md) w posiadaniu znaków zamiast typu ogólnego w typie obiektu wstawianego do strumienia wyjściowego.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*Chartype*\
Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartością domyślną jest **char**.

*Cechy*\
Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, `char_traits` \< a wartością domyślną jest *CharType>.*

## <a name="remarks"></a>Uwagi

Klasa ostreambuf_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane bezpośrednio do `ostreambuf_iterator`strumieni wyjściowych za pomocą . Klasa oferuje iterator strumienia niskiego poziomu, który umożliwia dostęp do surowego (niesformatowanego) strumienia we/wy w postaci znaków, a także możliwość ominięcia etapu buforowania i tłumaczenia znaków związanych z iteratorami strumienia wysokiego poziomu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Konstruuje `ostreambuf_iterator` zainicjowany, aby zapisać znaki do strumienia wyjściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ, który zawiera typ znaku `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, który zapewnia typ strumienia `ostream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, który zapewnia typ strumienia `ostreambuf_iterator`.|
|[traits_type](#traits_type)|Typ, który zawiera typ cech charakteru `ostream_iterator`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Nie powiodło się](#failed)|Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*](#op_star)|Operator dereferencing używany do implementacji \* `i`  =  `x`wyrażenia iteratora wyjściowego .|
|[operator++](#op_add_add)|Operator przyrostu niefunkcjonalnego, `ostreambuf_iterator` który zwraca do tego samego obiektu, który został rozwiązany przed wywołaniem operacji.|
|[operator=](#op_eq)|Operator wstawia znak do bufora skojarzonego strumienia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator::char_type

Typ, który zawiera typ znaku `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator::nie powiodło się

Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli żadne wstawienie do buforu strumienia wyjściowego nie powiodło się wcześniej; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **wartość true,** `operator=`jeśli w dowolnym wcześniejszym użyciu elementu `sputc` członkowskiego wywołanie **podf**_-> **zwrócone eof**.

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator::operator\*

Niefunkcjonalny operator dereferencing używany do \* implementacji wyrażenia iteratora wyjściowego *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Ostreambuf iterator obiektu.

### <a name="remarks"></a>Uwagi

Ten operator działa tylko \* w wyrażeniu iteratora wyjściowego *i* = *x* do znaków wyjściowych do buforu strumienia. Zastosowany do iteratora ostreambuf zwraca iteratora; iter zwraca **iter,** ** \***

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator::operator++

Operator przyrostu niefunkcjonalnego, który zwraca iteratora ostream do tego samego znaku, który został zaadresowany przed wywołaniem operacji.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do znaku pierwotnie zaadresowane lub do obiektu `ostreambuf_iterator` \< zdefiniowanego w implementacji, który jest konwertowany na **CharType**, **Cechy**>.

### <a name="remarks"></a>Uwagi

Operator jest używany do implementacji wyrażenia \* iteratora wyjściowego *i* = *x*.

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator::operator=

Operator wstawia znak do bufora skojarzonego strumienia.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parametry

*_Char*\
Znak, który ma zostać wstawiony do buforu strumienia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do znaku wstawionego do buforu strumienia.

### <a name="remarks"></a>Uwagi

Operator przypisania używany do implementacji \* wyrażenia iteratora wyjściowego *i* = *x* do zapisywania w strumieniu wyjściowym.

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator

Konstruuje `ostreambuf_iterator` zainicjowany, aby zapisać znaki do strumienia wyjściowego.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Wyjściowy streambuf obiekt używany do inicjowania wskaźnika buforu strumienia wyjściowego.

*Ostr*\
Obiekt strumienia wyjściowego używany do inicjowania wskaźnika buforu strumienia wyjściowego.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje wskaźnik wyjściowego buforu strumienia za pomocą *strbuf*.

Drugi konstruktor inicjuje wskaźnik wyjściowego buforu strumienia za pomocą pliku `Ostr`. `rdbuf`. Przechowywany wskaźnik nie może być wskaźnikiem zerowym.

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type

Typ, który zapewnia typ strumienia `ostream_iterator`.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basicOstream` \< **CharType**, **Cechy**>

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator,](#ostreambuf_iterator_ostreambuf_iterator) aby zapoznać się z `ostream_type`przykładem deklarowania i używania pliku .

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type

Typ, który zapewnia typ strumienia `ostreambuf_iterator`.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem `basic_streambuf` \< **CharType**, **Cechy**>, klasy strumienia dla buforów we/wy, który staje się, `streambuf` gdy specjalizuje się char typu znak . **char**

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator,](#ostreambuf_iterator_ostreambuf_iterator) aby zapoznać się z `streambuf_type`przykładem deklarowania i używania pliku .

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator::traits_type

Typ, który zawiera typ cech charakteru `ostream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Traits`szablonu .

### <a name="example"></a>Przykład

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
