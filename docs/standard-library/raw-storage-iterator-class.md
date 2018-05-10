---
title: raw_storage_iterator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
dev_langs:
- C++
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d6c93bfc6525840343c64b8cd804ddb65f68dd5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator — Klasa

Klasa adaptera, która jest dostarczana, aby umożliwić algorytmom zapisywanie ich wyników do pamięci niezainicjowanej.

## <a name="syntax"></a>Składnia

```cpp
template <class OutputIterator, class Type>
class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

`OutputIterator` Określa iteratora danych wyjściowych dla obiekt jest przechowywany.

*Typ* typ obiektu, dla którego jest przydzielane magazynu.

## <a name="remarks"></a>Uwagi

Klasa opisuje iterację wyjściowy, który konstruuje obiektów typu **typu** w sekwencji generuje. Obiekt klasy `raw_storage_iterator` \< **ForwardIterator**, **typu**> uzyskuje dostęp do magazynu za pośrednictwem obiektu do przodu iteratora klasy **ForwardIterator**, określ podczas konstruowania obiektu. Dla obiekt pierwszej klasy **ForwardIterator**, wyrażenie  **& \*pierwszy** musi wyznaczyć unconstructed magazynu dla obiekt dalej (typu **typu** ) w wygenerowanym sekwencji.

Ta klasa Adapter jest używana, gdy jest to niezbędne do oddzielania alokacją pamięci i konstrukcji obiektów. `raw_storage_iterator` Może służyć do kopii obiektów do niezainicjowanego magazynu, na przykład pamięci przydzielony przy użyciu `malloc` funkcji.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Tworzy iteratora czystego magazynu, z określonego źródłowego iteratora danych wyjściowych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[element_type](#element_type)|Zawiera typ, który opisuje element ma być przechowywany iteratora pojemności.|
|[iter_type](#iter_type)|Zawiera typ, który opisuje iteratora źródłową iteratora pojemności.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator usuwania odwołań, używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `ii`  =  `x`.|
|[operator=](#op_eq)|Operator przypisania używaną do zaimplementowania wyrażenia iteratora pojemności * `i`  =  `x` do przechowywania w pamięci.|
|[operator++](#op_add_add)|Operatory preincrement i postincrement dla Iteratory pojemności.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="element_type"></a>  raw_storage_iterator::ELEMENT_TYPE

Zawiera typ, który opisuje element ma być przechowywany iteratora pojemności.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu raw_storage_iterator — klasa **typu**.

## <a name="iter_type"></a>  raw_storage_iterator::iter_type

Zawiera typ, który opisuje iteratora źródłową iteratora pojemności.

```cpp
typedef ForwardIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **ForwardIterator**.

## <a name="op_star"></a>  raw_storage_iterator::operator *

Operator usuwania odwołań, używaną do zaimplementowania wyrażenia iteratora pojemności \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do iteratora pojemności

### <a name="remarks"></a>Uwagi

Wymagania dotyczące **ForwardIterator** to nieprzetworzonego iteratora magazynu muszą spełniać wymagają tylko wyrażenia \* *ii* = *t* można prawidłowe i że wyświetlany jest tekst nic o **operator** lub `operator=` samodzielnie. Zwraca operatorach elementów członkowskich w tej implementacji  **\*to**, dzięki czemu [operatora =](#op_eq)( **constType**&) można wykonywać rzeczywistego magazynu w wyrażeniu takie jak \* *ptr* = `val`.

### <a name="example"></a>Przykład

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
 *pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
 *it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_eq"></a>  raw_storage_iterator::operator =

Operator przypisania używaną do zaimplementowania wyrażenia iteratora pojemności \* *i* = *x* do przechowywania w pamięci.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

### <a name="parameters"></a>Parametry

`val` Wartość typu obiektu **typu** ma zostać wstawiony do pamięci.

### <a name="return-value"></a>Wartość zwracana

Wstawia operator `val` do pamięci, a następnie zwraca odwołanie do iteratora pojemności.

### <a name="remarks"></a>Uwagi

Wymagania dotyczące **ForwardIterator** stan, który muszą spełniać iteratora pojemności wymagają tylko wyrażenia \* *ii* = *t* można prawidłowy, i że wyświetlany jest tekst nic o **operator** lub `operator=` samodzielnie. Zwraca tych operatorów Członkowskich  **\*to**.

Operator przypisania konstruuje następny obiekt w sekwencji danych wyjściowych przy użyciu wartości przechowywanych iteratora najpierw wyniku obliczenia wyrażenia nowego umieszczania **nowe** (( `void` \*) &\* **pierwszy**) **typu**( `val`).

### <a name="example"></a>Przykład

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
 *it = 5;
}
\* Output:
Not constructed.
Copying 5
Constructing 5
*\
```

## <a name="op_add_add"></a>  raw_storage_iterator::operator ++

Operatory preincrement i postincrement dla Iteratory pojemności.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Iteratora pojemności lub odwołanie do iteratora pojemności.

### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i zapisania obiektu typu **CharType** ze strumienia wejściowego skojarzone. Drugi operator tworzy kopię obiektu, zwiększa obiektu, a następnie zwraca kopii.

Pierwszy operator preincrement zwiększa obiektu iteratora przechowywanych danych wyjściowych, a następnie zwraca  **\*to**.

Drugi operator postincrement tworzy kopię  **\*to**, zwiększa obiektu iteratora przechowywanych danych wyjściowych, a następnie zwraca kopii.

Magazyny konstruktora **pierwszy** jako dane wyjściowe obiektu iteratora.

### <a name="example"></a>Przykład

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
 *it = 2 * i;
};

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
\* Output:
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
*\
```

## <a name="raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator

Tworzy iteratora czystego magazynu, z określonego źródłowego iteratora danych wyjściowych.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

### <a name="parameters"></a>Parametry

`first` Iteratora do przodu, który ma opierają się `raw_storage_iterator` obiekt tworzona.

### <a name="example"></a>Przykład

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
\* Output:
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
*\
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
