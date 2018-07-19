---
title: Klasa ostreambuf_iterator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
dev_langs:
- C++
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d26ecc120565556651057b764a5fdd7ae64d43
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958256"
---
# <a name="ostreambufiterator-class"></a>Klasa ostreambuf_iterator

Klasa szablonu ostreambuf_iterator opisuje obiekt iteratora wyjściowego, który zapisuje kolejne elementy znaków do strumienia wyjściowego przy użyciu wyodrębniania **operator >>**. `ostreambuf_iterator`s różnią się od [ostream_iterator — klasa](../standard-library/ostream-iterator-class.md) że mają znaki zamiast typu rodzajowego na typ obiektu, jest wstawiany do strumienia wyjściowego.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parametry

*CharType* typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to **char**.

*Cechy* typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType >.*

## <a name="remarks"></a>Uwagi

Klasa ostreambuf_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być pisane bezpośrednio do wyjściowych strumieni za pomocą `ostreambuf_iterator`. Klasa oferuje iterator strumienia niskiego poziomu, który umożliwia dostęp do surowego (niesformatowanego) strumienia we/wy w postaci znaków, a także możliwość ominięcia etapu buforowania i tłumaczenia znaków związanych z iteratorami strumienia wysokiego poziomu.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Konstruuje `ostreambuf_iterator` który jest inicjowany do zapisu znaków do strumienia wyjściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zapewnia typ znaków `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, który zapewnia typ ciągu `ostream_iterator`.|
|[streambuf_type](#streambuf_type)|Typ, który zapewnia typ ciągu `ostreambuf_iterator`.|
|[traits_type](#traits_type)|Typ, który zapewnia typ cechy znaków `ostream_iterator`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Nie powiodło się](#failed)|Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator dereferencji używany do implementowania wyrażenie iteratora wyjściowego * `i`  =  `x`.|
|[operator++](#op_add_add)|Operator inkrementacji prawidłowo, który zwraca `ostreambuf_iterator` ten sam obiekt się odnosił przed wywołaniem operacji.|
|[operator=](#op_eq)|Operator wstawia znak do bufora skojarzonego strumienia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="char_type"></a>  ostreambuf_iterator::char_type

Typ, który zapewnia typ znaków `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `CharType`.

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
\* Output:
The characters written to the output stream
 by charOutBuf are: OUT.
*\
```

## <a name="failed"></a>  ostreambuf_iterator::failed

Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli nie wstawiania do bufora strumienia wyjściowego nie powiodło się wcześniej; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **true** , gdy w wszystkie wcześniejsze zastosowanie elementu członkowskiego `operator=`, wywołanie **subf**-> _ `sputc` zwrócił **eof**.

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
\* Output:
abc are characters output individually.
No insertions failed.
*\
```

## <a name="op_star"></a>  ostreambuf_iterator::operator *

Prawidłowo operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt iteratora ostreambuf.

### <a name="remarks"></a>Uwagi

Ten operator działa tylko w przypadku wyrażenia iteratora danych wyjściowych \* *i* = *x* do znaków danych wyjściowych do buforu strumienia. Stosowane do iteratora ostreambuf, zwraca iterator;  **\*iter** zwraca **iter**,

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="op_add_add"></a>  ostreambuf_iterator::operator ++

Operator inkrementacji prawidłowo, który zwraca ostream iterator do takiego samego znaku, którego się odnosił przed wykonaniem operacji została wywołana.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do znaku pierwotnie rozwiązane lub do zdefiniowanych w implementacji obiektu, który jest konwertowany na `ostreambuf_iterator` \< **CharType**, **cech**>.

### <a name="remarks"></a>Uwagi

Operator jest używany do implementowania wyrażenia iteratora danych wyjściowych \* *i* = *x*.

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="op_eq"></a>  ostreambuf_iterator::operator =

Operator wstawia znak do bufora skojarzonego strumienia.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parametry

*_Char* znak, który ma zostać wstawiony do buforu strumienia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do znaku wstawione do buforu strumienia.

### <a name="remarks"></a>Uwagi

Operator przypisania używany do implementowania wyrażenia iteratora danych wyjściowych \* *i* = *x* do zapisywania do strumienia wyjściowego.

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
\* Output:
Elements written to output stream:
OUT
*\
```

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator

Konstruuje `ostreambuf_iterator` który jest inicjowany do zapisu znaków do strumienia wyjściowego.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parametry

*strbuf* obiekt streambuf danych wyjściowych, które są używane do zainicjowania wskaźnika bufora strumienia wyjściowego.

*OSTR* obiekt strumienia wyjściowego, które są używane do zainicjowania wskaźnika bufora strumienia wyjściowego.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnika buforu strumienia wyjściowego przy użyciu *strbuf*.

Drugi Konstruktor inicjuje wskaźnika buforu strumienia wyjściowego przy użyciu `Ostr`. `rdbuf`. Przechowywany wskaźnik nie może być wskaźnikiem typu null.

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
\* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*\
```

## <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type

Typ, który zapewnia typ ciągu `ostream_iterator`.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basicOstream` \< **CharType**, **cech**>

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) przykładowy sposób deklarowania i użyj `ostream_type`.

## <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type

Typ, który zapewnia typ ciągu `ostreambuf_iterator`.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basic_streambuf` \< **CharType**, **cech**>, klasa strumienia dla buforów we/wy, która staje się `streambuf` podczas wyspecjalizowane typ znaku **char**.

### <a name="example"></a>Przykład

Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) przykładowy sposób deklarowania i użyj `streambuf_type`.

## <a name="traits_type"></a>  ostreambuf_iterator::traits_type

Typ, który zapewnia typ cechy znaków `ostream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Traits`.

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
\* Output:
The characters written to the output stream
 by charOutBuf are: OUT.
*\
```

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
