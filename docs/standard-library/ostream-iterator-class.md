---
title: ostream_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: a0c794fe2ff7897bcb6d6412613689100a977589
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373597"
---
# <a name="ostream_iterator-class"></a>ostream_iterator — Klasa

Szablon klasy ostream_iterator opisuje obiekt iteratora wyjściowego, który zapisuje kolejne `operator <<`elementy na strumieniu wyjściowym z wyodrębnianie .

## <a name="syntax"></a>Składnia

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Typu*\
Typ obiektu, który ma zostać wstawiony do strumienia wyjściowego.

*Chartype*\
Typ reprezentujący typ znaku `ostream_iterator`dla . Ten argument jest opcjonalny, a wartością domyślną jest **char**.

*Cechy*\
Typ reprezentujący typ znaku `ostream_iterator`dla . Ten argument jest opcjonalny, `char_traits` \< a wartością domyślną jest *CharType>.*

Klasa ostream_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane bezpośrednio do `ostream_iterator`strumieni wyjściowych za pomocą .

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostream_iterator](#ostream_iterator)|Tworzy, `ostream_iterator` który jest inicjowany i rozdzielane do zapisu do strumienia wyjściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Typ, który zawiera typ znaku `ostream_iterator`.|
|[ostream_type](#ostream_type)|Typ, który zapewnia typ strumienia `ostream_iterator`.|
|[traits_type](#traits_type)|Typ, który zawiera typ cech charakteru `ostream_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator*](#op_star)|Operator dereferencing używany do implementacji \* `i`  =  `x`wyrażenia iteratora wyjściowego .|
|[operator++](#op_add_add)|Operator przyrostu niefunkcjonalnego, `ostream_iterator` który zwraca do tego samego obiektu, który został rozwiązany przed wywołaniem operacji.|
|[operator=](#op_eq)|Operator przypisania używany do implementacji \* `i`  =  `x` wyrażenia iteratora wyjściowego do zapisu w strumieniu danych wyjściowych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator::char_type

Typ, który zapewnia typ znaku iteratora.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `CharType`szablonu .

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator::operator*

Operator dereferencing używany do implementacji \* wyrażenia iteratora wyjściowego *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odniesienie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Wymagania dla iteratora wyjściowego, `ostream_iterator` który musi \* spełniać wymagają tylko wyrażenie *ii* = *t* być prawidłowe i nic nie mówi o **operatora** lub `operator=` na własną rękę. Operator elementu członkowskiego w ** \*** tej implementacji zwraca to .

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator::operator++

Operator przyrostu niefunkcjonalnego, `ostream_iterator` który zwraca do tego samego obiektu, który został rozwiązany przed wywołaniem operacji.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odniesienie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Te operatory ** \*** członkowskie zarówno zwrócić ten .

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator::operator=

Operator przypisania używany do implementowania wyrażenia \* `i`  =  `x` output_iterator do zapisu w strumieniu danych wyjściowych.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*\
Wartość obiektu typu, `Type` który ma zostać wstawiony do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Operator wstawia *val* do strumienia wyjściowego skojarzonego z obiektem, a następnie ogranicznik określony w [konstruktorze ostream_iterator](#ostream_iterator) (jeśli istnieje), a następnie zwraca odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Wymagania dla iteratora wyjściowego, który `ostream_iterator` musi \* `ii`  =  spełniać wymagają tylko wyrażenie `t` są prawidłowe i nic nie mówi o operatora lub operatora = na własną rękę. Ten operator `*this`elementu członkowskiego zwraca .

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator::ostream_iterator

Tworzy, `ostream_iterator` który jest inicjowany i rozdzielane do zapisu do strumienia wyjściowego.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

*_Ostr*\
Strumień wyjściowy typu [ostream_iterator::ostream_type](#ostream_type) do iterowania.

*_Delimiter*\
Ogranicznik, który jest wstawiany do strumienia wyjściowego między wartościami.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje wskaźnik `&_Ostr`strumienia wyjściowego za pomocą pliku . Wskaźnik ciągu ogranicznika wyznacza pusty ciąg.

Drugi konstruktor inicjuje wskaźnik `&_Ostr` strumienia wyjściowego z i wskaźnik ciągu ogranicznika z *_Delimiter*.

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator::ostream_type

Typ, który zapewnia typ strumienia iteratora.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, klasy strumienia hierarchii iostream, która definiuje obiekty, które mogą być używane do pisania.

### <a name="example"></a>Przykład

Zobacz [ostream_iterator,](#ostream_iterator) aby zapoznać się z `ostream_type`przykładem deklarowania i używania pliku .

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator::traits_type

Typ, który zapewnia typ cech charakteru iteratora.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru `Traits`szablonu .

### <a name="example"></a>Przykład

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>Zobacz też

[\<>iteratora](../standard-library/iterator.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
