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
ms.openlocfilehash: cebe127eb985e564289db100fa56b0b979104819
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447090"
---
# <a name="ostreamiterator-class"></a>ostream_iterator — Klasa

Klasa szablonu ostream_iterator opisuje obiekt iteratora wyjściowego, który zapisuje kolejne elementy do strumienia wyjściowego przy użyciu wyodrębniania `operator <<`.

## <a name="syntax"></a>Składnia

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ obiektu, który ma zostać wstawiony do strumienia wyjściowego.

*CharType*\
Typ, który reprezentuje typ znaku dla `ostream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to **char**.

*Cech*\
Typ, który reprezentuje typ znaku dla `ostream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType >.*

Klasa ostream_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane bezpośrednio w strumieniach wyjściowych przy użyciu `ostream_iterator`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostream_iterator](#ostream_iterator)|Tworzy obiekt `ostream_iterator` , który jest zainicjowany i rozdzielony do zapisu w strumieniu wyjściowym.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zapewnia typ `ostream_iterator`znaku.|
|[ostream_type](#ostream_type)|Typ, który zapewnia typ `ostream_iterator`strumienia.|
|[traits_type](#traits_type)|Typ, który zapewnia dla typu `ostream_iterator`cechy znakowe.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do \* implementowania wyrażenia `i`  =  `x`iteratora danych wyjściowych.|
|[operator++](#op_add_add)|Niefunkcjonalny operator przyrostu zwracający `ostream_iterator` do tego samego obiektu, do którego odnosił się przed wywołaniem operacji.|
|[operator=](#op_eq)|Operator przypisania używany do \* implementowania wyrażenia `i`  =  `x` iteratora danych wyjściowych do zapisu w strumieniu wyjściowym.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> iteratora

**Przestrzeń nazw:** std

## <a name="char_type"></a>ostream_iterator::char_type

Typ, który zapewnia typ znaku iteratora.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `CharType`szablonu.

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

## <a name="op_star"></a>ostream_iterator:: operator *

Operator dereferencji używany do \* implementowania wyrażenia iteratora danych wyjściowych *II* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Wymagania dla iteratora danych wyjściowych, `ostream_iterator` które muszą spełniać, wymagają, \* aby tylko wyrażenie *II* =  `operator=` *t* było prawidłowe i nie zachodzi niczego o **operator** lub samodzielnie. Operator elementu członkowskiego w tej implementacji zwraca  **\*ten**element.

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

## <a name="op_add_add"></a>ostream_iterator:: operator + +

Niefunkcjonalny operator przyrostu zwracający `ostream_iterator` do tego samego obiektu, do którego odnosił się przed wywołaniem operacji.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `ostream_iterator`.

### <a name="remarks"></a>Uwagi

Te operatory elementów członkowskich zwracają  **\*tę**funkcję.

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

## <a name="op_eq"></a>ostream_iterator:: operator =

Operator przypisania używany do \* implementowania wyrażenia `i`  =  `x` output_iterator do zapisywania w strumieniu wyjściowym.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parametry

*użyte*\
Wartość obiektu typu `Type` , który ma zostać wstawiony do strumienia wyjściowego.

### <a name="return-value"></a>Wartość zwracana

Operator wstawia wartość *Val* do strumienia wyjściowego skojarzonego z obiektem, po którym następuje ogranicznik określony w [konstruktorze ostream_iterator](#ostream_iterator) (jeśli istnieje), a następnie zwraca `ostream_iterator`odwołanie do.

### <a name="remarks"></a>Uwagi

Wymagania dla iteratora danych wyjściowych, `ostream_iterator` które muszą spełniać, wymagają, \* aby tylko wyrażenie `ii`  =  `t` było prawidłowe, i nie niczego więcej na temat operatora ani operatora = samodzielnie. Ten operator elementu członkowskiego zwraca `*this`.

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

## <a name="ostream_iterator"></a>ostream_iterator::ostream_iterator

Tworzy obiekt `ostream_iterator` , który jest zainicjowany i rozdzielony do zapisu w strumieniu wyjściowym.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parametry

*_Ostr*\
Strumień wyjściowy typu [ostream_iterator:: ostream_type](#ostream_type) , który ma zostać powtórzony.

*_Delimiter*\
Ogranicznik wstawiony do strumienia wyjściowego między wartościami.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnik strumienia wyjściowego przy użyciu `&_Ostr`. Wskaźnik ciągu ogranicznika wyznacza pusty ciąg.

Drugi Konstruktor inicjuje wskaźnik strumienia wyjściowego ze znakiem `&_Ostr` i ogranicznikiem ciągu z *_Delimiter*.

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

## <a name="ostream_type"></a>ostream_iterator::ostream_type

Typ, który zapewnia typ strumienia iteratora.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, klasy strumienia hierarchii iostream, która definiuje obiekty, które mogą być używane do pisania.

### <a name="example"></a>Przykład

Zobacz [ostream_iterator](#ostream_iterator) , aby zapoznać się z przykładem sposobu deklarowania i używania `ostream_type`.

## <a name="traits_type"></a>ostream_iterator::traits_type

Typ, który zapewnia typ cechy znakowej iteratora.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `Traits`szablonu.

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

## <a name="see-also"></a>Zobacz także

[\<iterator>](../standard-library/iterator.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
