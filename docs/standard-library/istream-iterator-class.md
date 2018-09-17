---
title: istream_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
dev_langs:
- C++
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8da58ad4ba2ddbfdbea7a951104b88d8f55c445
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710290"
---
# <a name="istreamiterator-class"></a>istream_iterator — Klasa

Opisuje obiekt iteratora wejściowego. Wyodrębnia obiekty klasy `Type` ze strumienia wejściowego, który uzyskuje dostęp przez obiekt, który przechowuje, typu `pointer` do `basic_istream` <  `CharType`, `Traits`>.

## <a name="syntax"></a>Składnia

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ obiektu, który ma zostać wyodrębniony ze strumienia wejściowego.

*CharType*<br/>
Typ, który reprezentuje typ znaków dla `istream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to **char**.

*Cechy*<br/>
Typ, który reprezentuje typ znaków dla `istream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` <  `CharType`>.

*odległość*<br/>
A podpisany typ całkowity, który reprezentuje typ różnicy dla `istream_iterator`. Ten argument jest opcjonalny, a wartość domyślna to `ptrdiff_t`.

Po skonstruowaniu lub inkrementacji obiektu klasy istream_iterator z przechowywanym wskaźnikiem innym niż null, obiekt próbuje wyodrębnić i przechowywać obiekt typu `Type` ze skojarzonego strumienia wejściowego. Jeśli wyodrębnienie się nie uda, obiekt skutecznie zastępuje przechowywany wskaźnik wskaźnikiem pustym, tworząc wskaźnik końca sekwencji.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[istream_iterator](#istream_iterator)|Konstruuje albo iterator koniec strumienia jako domyślny `istream_iterator` lub `istream_iterator` inicjowany do typu strumienia iteratora, z którego odczytuje.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Typ, który zapewnia typ znaków `istream_iterator`.|
|[istream_type](#istream_type)|Typ, który zapewnia typ ciągu `istream_iterator`.|
|[traits_type](#traits_type)|Typ, który zapewnia typ cechy znaków `istream_iterator`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator dereferencji zwraca przechowywany obiekt typu `Type` odnoszącego `istream_iterator`.|
|[operator ->](#op_arrow)|Zwraca wartość elementu członkowskiego, jeśli istnieje.|
|[operator++](#op_add_add)|Albo wyodrębnia inkrementowany obiekt ze strumienia wejściowego, albo kopiuje obiekt przed jego inkrementacją i zwraca kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iterator >

**Namespace:** standardowe

## <a name="char_type"></a>  istream_iterator::char_type

Typ, który zapewnia typ znaków `istream_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Chartype`.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iterator"></a>  istream_iterator::istream_iterator

Konstruuje albo iterator koniec strumienia jako domyślny `istream_iterator` lub `istream_iterator` inicjowany do typu strumienia iteratora, z którego odczytuje.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parametry

*_Istr*<br/>
Strumień wejściowy odczyt Użyj zainicjować `istream_iterator`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje wskaźnik strumienia wejściowego z pustym wskaźnikiem i tworzy iterator, koniec strumienia. Drugi Konstruktor inicjuje wskaźnik strumienia wejściowego z *& _Istr*, następnie próbuje wyodrębnić i przechowywać obiekt typu `Type`.

Koniec strumienia iteratora, może służyć do testowania czy `istream_iterator` osiągnięto koniec strumienia.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_type"></a>  istream_iterator::istream_type

Typ, który zapewnia typ ciągu `istream_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla `basic_istream` \< **CharType**, **cech**>.

### <a name="example"></a>Przykład

Zobacz [istream_iterator](#istream_iterator) przykładowy sposób deklarowania i użyj `istream_type`.

## <a name="op_star"></a>  istream_iterator::operator *

Operator dereferencji zwraca przechowywany obiekt typu `Type` odnoszącego `istream_iterator`.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt typu `Type`.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_arrow"></a>  istream_iterator::operator-&gt;

Zwraca wartość elementu członkowskiego, jeśli istnieje.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość elementu członkowskiego, jeśli istnieje.

### <a name="remarks"></a>Uwagi

`i->m` jest odpowiednikiem `(*i).m`

Operator zwraca `&*this`.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_add_add"></a>  istream_iterator::operator ++

Albo wyodrębnia inkrementowany obiekt ze strumienia wejściowego, albo kopiuje obiekt przed jego inkrementacją i zwraca kopię.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy operator członkowski zwraca odwołanie do inkrementowany obiekt typu `Type` wyodrębnione ze strumienia wejściowego i drugi element członkowski funkcja zwraca kopię obiektu.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="traits_type"></a>  istream_iterator::traits_type

Typ, który zapewnia typ cechy znaków `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *cech*.

### <a name="example"></a>Przykład

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>Zobacz także

[input_iterator_tag, struktura](../standard-library/input-iterator-tag-struct.md)<br/>
[iterator, struktura](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
