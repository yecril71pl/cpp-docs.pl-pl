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
ms.openlocfilehash: e4e21bd0c1323afdc2c81a0e581c3557b8040193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202444"
---
# <a name="ostreambuf_iterator-class"></a>Klasa ostreambuf_iterator

Szablon klasy ostreambuf_iterator opisuje obiekt iteratora wyjściowego, który zapisuje kolejne elementy znaku w strumieniu wyjściowym z **operatorem **ekstrakcji>>. `ostreambuf_iterator`S różni się od elementów [klasy ostream_iterator](../standard-library/ostream-iterator-class.md) w postaci znaków, a nie typu ogólnego w typie obiektu wstawianym do strumienia wyjściowego.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to **`char`** .

*Cech*\
Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType> . *

## <a name="remarks"></a>Uwagi

Klasa ostreambuf_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane bezpośrednio w strumieniach wyjściowych przy użyciu `ostreambuf_iterator` . Klasa oferuje iterator strumienia niskiego poziomu, który umożliwia dostęp do surowego (niesformatowanego) strumienia we/wy w postaci znaków, a także możliwość ominięcia etapu buforowania i tłumaczenia znaków związanych z iteratorami strumienia wysokiego poziomu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Tworzy obiekt `ostreambuf_iterator` , który jest zainicjowany, aby pisać znaki do strumienia wyjściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zapewnia typ znaku `ostreambuf_iterator` .|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, który zapewnia typ strumienia `ostream_iterator` .|
|[streambuf_type](#streambuf_type)|Typ, który zapewnia typ strumienia `ostreambuf_iterator` .|
|[traits_type](#traits_type)|Typ, który zapewnia dla typu cechy znakowe `ostream_iterator` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[awarii](#failed)|Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* `i`  =  `x` .|
|[operator + +](#op_add_add)|Niefunkcjonalny operator przyrostu zwracający `ostreambuf_iterator` do tego samego obiektu, do którego odnosił się przed wywołaniem operacji.|
|[operator =](#op_eq)|Operator wstawia znak do bufora skojarzonego strumienia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<iterator>

**Przestrzeń nazw:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator:: char_type

Typ, który zapewnia typ znaku `ostreambuf_iterator` .

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType` .

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

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator:: nie powiodło się

Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli nie można wstawić do buforu strumienia wyjściowego wcześniej; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **`true`** Jeśli w dowolnym poprzednim użyciu elementu członkowskiego `operator=` wywołanie **subf**_-> `sputc` zwróciło **znacznik EOF**.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator:: operator\*

Niefunkcjonalny operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* *i*  =  *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt iteratora ostreambuf.

### <a name="remarks"></a>Uwagi

Ten operator działa tylko w wyrażeniu iteratora danych wyjściowych \* *i*  =  *x* do znaków wyjściowych do buforu strumienia. Zastosowano do iteratora ostreambuf, zwraca iterator; ** \* ITER** zwraca **ITER**,

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator:: operator + +

Niefunkcjonalny operator przyrostu zwracający iterator ostream do tego samego znaku, który jest adresowany przed wywołaniem operacji.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do znaku pierwotnie dotyczyło lub do obiektu zdefiniowanego przez implementację, który jest konwertowany na `ostreambuf_iterator` \< **CharType**, **Traits**> .

### <a name="remarks"></a>Uwagi

Operator służy do implementowania wyrażenia iteratora danych wyjściowych \* *i*  =  *x*.

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

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator:: operator =

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

Operator przypisania używany do implementowania wyrażenia iteratora wyjściowego \* *i*  =  *x* do zapisu w strumieniu wyjściowym.

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

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator:: ostreambuf_iterator

Tworzy obiekt `ostreambuf_iterator` , który jest zainicjowany, aby pisać znaki do strumienia wyjściowego.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf*\
Wyjściowy obiekt streambuf używany do inicjowania wskaźnika wyjściowego buforu strumienia.

*Ostr*\
Obiekt strumienia wyjściowego używany do inicjowania wskaźnika buforu wyjściowego strumienia.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnik bufora strumienia wyjściowego z *strbuf*.

Drugi Konstruktor inicjuje wskaźnik bufora strumienia wyjściowego z `Ostr` . `rdbuf`. Składowany wskaźnik nie może być pustym wskaźnikiem.

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

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator:: ostream_type

Typ, który zapewnia typ strumienia `ostream_iterator` .

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla`basicOstream`\< **CharType**, **Traits**>

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) , aby zapoznać się z przykładem sposobu deklarowania i używania `ostream_type` .

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator:: streambuf_type

Typ, który zapewnia typ strumienia `ostreambuf_iterator` .

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basic_streambuf` \< **CharType**, **Traits**> , klasy strumienia dla buforów we/wy, które staną się `streambuf` nieskomplikowane dla typu znaku **`char`** .

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) , aby zapoznać się z przykładem sposobu deklarowania i używania `streambuf_type` .

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator:: traits_type

Typ, który zapewnia dla typu cechy znakowe `ostream_iterator` .

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Traits` .

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

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
