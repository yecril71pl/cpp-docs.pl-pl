---
title: ostream_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49626cbb33ed1220ad82cbec10ad675769b054d6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ostreamiterator-class"></a>ostream_iterator — Klasa

Ostream_iterator — klasa szablonu opisuje obiekt iteratora wyjściowy, który zapisuje kolejne elementy do strumienia wyjściowego o wyodrębnianiu **operator <<**.

## <a name="syntax"></a>Składnia

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Typ* typ obiektu, które ma zostać wstawiony do strumienia wyjściowego.

`CharType` Typ reprezentujący typ znaków `ostream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to `char`.

`Traits` Typ reprezentujący typ znaków `ostream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType >.*

Klasa ostream_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane dane bezpośrednio do danych wyjściowych strumieni przy użyciu `ostream_iterator`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostream_iterator](#ostream_iterator)|Konstruuje `ostream_iterator` czyli zainicjować i ograniczony do zapisu do strumienia wyjściowego.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zawiera znak typu `ostream_iterator`.|
|[ostream_type](#ostream_type)|Typ, który udostępnia dla typu strumienia `ostream_iterator`.|
|[traits_type](#traits_type)|Typ, który zawiera typ cech znaków `ostream_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x`.|
|[operator++](#op_add_add)|Operator inkrementacji prawidłowo, który zwraca `ostream_iterator` do tego samego obiektu adresowane, zanim została wywołana w operacji.|
|[operator=](#op_eq)|Operator przypisania używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` do zapisywania do strumienia wyjściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="char_type"></a>  ostream_iterator::char_type

Typ, który zawiera typ znakowy iteratora.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **CharType**.

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
\* Output:
The integers written to the output stream
by intOut are:
10
20
30
*\
```

## <a name="op_star"></a>  ostream_iterator::operator *

Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe \* *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Wymagania dotyczące iteratora dane wyjściowe który `ostream_iterator` muszą spełniać wymagają tylko wyrażenia \* *ii* = *t* ważność i mówi nic o **operator** lub `operator=` samodzielnie. Zwraca element członkowski operatora w tej implementacji  **\*to**.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_add_add"></a>  ostream_iterator::operator ++

Operator inkrementacji prawidłowo, który zwraca `ostream_iterator` do tego samego obiektu adresowane, zanim została wywołana w operacji.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Zwraca te operatorów Członkowskich zarówno  **\*to**.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="op_eq"></a>  ostream_iterator::operator =

Operator przypisania używaną do zaimplementowania wyrażenie output_iterator * `i`  =  `x` do zapisywania do strumienia wyjściowego.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Wartość typu obiektu `Type` ma zostać wstawiony do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Wstawia — operator `val` do strumienia wyjściowego skojarzony z obiektem, a następnie Ogranicznik podany w [ostream_iterator — Konstruktor](#ostream_iterator) (jeśli istnieje), a następnie zwraca odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Wymagania dotyczące iteratora dane wyjściowe który `ostream_iterator` muszą spełniać wymagają tylko wyrażenie * `ii`  =  `t` ważność i mówi nic o operator lub operator = samodzielnie. Ten operator członkowski zwraca `*this`.

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
\* Output:
Elements written to output stream:
10
20
30
*\
```

## <a name="ostream_iterator"></a>  ostream_iterator::ostream_iterator

Konstruuje `ostream_iterator` czyli zainicjować i ograniczony do zapisu do strumienia wyjściowego.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

`_Ostr` Strumień wyjściowy typu [ostream_iterator::ostream_type](#ostream_type) należy powtórzyć za pośrednictwem.

`_Delimiter` Ogranicznik, które są wstawiane do strumienia wyjściowego między wartościami.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnik strumienia danych wyjściowych z `&_Ostr`. Wskaźnik ciągu ogranicznik wyznacza ciągiem pustym.

Drugi Konstruktor inicjuje wskaźnika strumienia wyjściowego za pomocą `&_Ostr` i wskaźnikiem do ciągu ogranicznik z `_Delimiter`.

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
\* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*\
```

## <a name="ostream_type"></a>  ostream_iterator::ostream_type

Typ, który udostępnia dla typu strumienia iteratora.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [basic_ostream —](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, klasę strumienia hierarchii iostream definiuje obiekty, które mogą służyć do zapisu.

### <a name="example"></a>Przykład

Zobacz [ostream_iterator —](#ostream_iterator) przykład sposobu deklarowanie i użycie `ostream_type`.

## <a name="traits_type"></a>  ostream_iterator::traits_type

Typ, który zawiera znak cech typu iteratora.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **cech**.

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
\* Output:
The integers written to output stream
by intOut are:
1
10
100
*\
```

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
