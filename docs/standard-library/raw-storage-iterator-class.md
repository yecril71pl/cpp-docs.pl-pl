---
title: raw_storage_iterator — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: 8e13d03e577df4c64e85704993cfc0ff81af5f8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503015"
---
# <a name="rawstorageiterator-class"></a>raw_storage_iterator — Klasa

Klasa adaptera, która jest dostarczana, aby umożliwić algorytmom zapisywanie ich wyników do pamięci niezainicjowanej.

## <a name="syntax"></a>Składnia

```cpp
template <class OutputIterator, class Type>
class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

*OutputIterator*<br/>
Określa iterator danych wyjściowych dla obiektu są przechowywane.

*Typ*<br/>
Typ obiektu, dla którego Magazyn jest przydzielany.

## <a name="remarks"></a>Uwagi

Klasa opisuje iterator danych wyjściowych, który tworzy obiekty typu `Type` w sekwencji, generuje ona. Obiekt klasy `raw_storage_iterator` \< **ForwardIterator**, **typu**> uzyskuje dostęp do magazynu za pośrednictwem obiektu iterator do przodu, klasy `ForwardIterator`, że możesz określić, kiedy należy Skonstruuj obiekt. Dla obiektu pierwszej klasy `ForwardIterator`, wyrażenie  **& \*pierwszy** należy wyznaczyć unconstructed magazynu na potrzeby następnego obiektu (typu `Type`) w wygenerowanym sekwencji.

Ta klasa adaptera jest używana, gdy jest to konieczne oddzielać alokacji pamięci od konstrukcji obiektu. `raw_storage_iterator` Może służyć do skopiowania obiektów do niezainicjowanego magazynu, takich jak pamięci przydzielonej za pomocą `malloc` funkcji.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Tworzy iterator magazynu przy użyciu określonego podstawowy iterator danych wyjściowych.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[element_type](#element_type)|Zapewnia, że typ, który opisuje element ma być przechowywany iterator magazynu.|
|[iter_type](#iter_type)|Zawiera typ, który opisuje iterator, która jest podporządkowana narzędziu iteratora magazynu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator *](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* `ii`  =  `x`.|
|[operator=](#op_eq)|Operator przypisania używany do implementowania wyrażenia iteratora magazynu \* `i`  =  `x` do przechowywania w pamięci.|
|[operator++](#op_add_add)|Operatory preincrement i postinkrementacyjne dla iteratorów magazynu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="element_type"></a>  raw_storage_iterator::ELEMENT_TYPE

Zapewnia, że typ, który opisuje element ma być przechowywany iterator magazynu.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu raw_storage_iterator — klasa `Type`.

## <a name="iter_type"></a>  raw_storage_iterator::iter_type

Zawiera typ, który opisuje iterator, która jest podporządkowana narzędziu iteratora magazynu.

```cpp
typedef ForwardIterator iter_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `ForwardIterator`.

## <a name="op_star"></a>  raw_storage_iterator::operator\*

Operator dereferencji używany do implementowania wyrażenia iteratora magazynu \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do iteratora magazynu

### <a name="remarks"></a>Uwagi

Wymagania dotyczące `ForwardIterator` są który nieprzetworzonych magazynu iteratora musi spełniać wymagają tylko wyrażenia \* *ii* = *t* ważność i mówi nic o **operator** lub `operator=` własnych. Zwraca operatory elementów członkowskich w tej implementacji  **\*to**, dzięki czemu [operator =](#op_eq)(**constType**&) można wykonywać rzeczywisty magazyn w wyrażeniu takie jak \* *ptr* = `val`.

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
/* Output:
Not constructed.
Copying 5
Constructing 5
*/
```

## <a name="op_eq"></a>  raw_storage_iterator::operator =

Operator przypisania używany do implementowania wyrażenia iteratora magazynu \* *i* = *x* do przechowywania w pamięci.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość obiektu typu `Type` ma zostać wstawiony do pamięci.

### <a name="return-value"></a>Wartość zwracana

Wstawia operator `val` do pamięci, a następnie zwraca odwołanie do iteratora magazynu.

### <a name="remarks"></a>Uwagi

Wymagania dotyczące `ForwardIterator` stan, który musi spełniać iteratora magazynu wymaga tylko wyrażenia \* *ii* = *t* był prawidłowy, i mówi nic o **operator** lub `operator=` własnych. Te operatory elementu członkowskiego zwraca  **\*to**.

Operator przypisania tworzy następny obiekt w sekwencji wyjścia, przy użyciu wartości przechowywanego iteratora, a po pierwsze, w wyniku obliczenia wyrażenia nowego położenia **nowe** (( `void` \*) &\* **pierwszy**) **typu**( `val`).

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
/* Output:
Not constructed.
Copying 5
Constructing 5
*/
```

## <a name="op_add_add"></a>  raw_storage_iterator::operator ++

Operatory preincrement i postinkrementacyjne dla iteratorów magazynu.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Iterator magazynu lub odwołanie do iteratora magazynu.

### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i przechowywać obiekt typu `CharType` ze skojarzonego strumienia wejściowego. Drugi operator tworzy kopię obiektu, zwiększa obiektu, a następnie zwraca kopię.

Pierwszy operator preincrement zwiększa obiekt iteratora danych wyjściowych przechowywanych, a następnie zwraca  **\*to**.

Drugi operator postinkrementacyjne tworzy kopię  **\*to**, zwiększa obiekt iteratora danych wyjściowych przechowywanych, a następnie zwraca kopię.

Magazyny Konstruktor `first` jako obiekt iteratora wyjściowego.

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
/* Output:
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
*/
```

## <a name="raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator

Tworzy iterator magazynu przy użyciu określonego podstawowy iterator danych wyjściowych.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator do przodu, który jest podstawą `raw_storage_iterator` obiekt jest konstruowany.

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
/* Output:
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
*/
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
