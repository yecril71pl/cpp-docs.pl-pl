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
ms.openlocfilehash: e5423d3b0801570167e1e0424aad18b9e8f74e7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831427"
---
# <a name="raw_storage_iterator-class"></a>raw_storage_iterator — Klasa

Klasa adaptera, która jest dostarczana, aby umożliwić algorytmom zapisywanie ich wyników do pamięci niezainicjowanej.

## <a name="syntax"></a>Składnia

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parametry

*OutputIterator*\
Określa iterator danych wyjściowych dla przechowywanego obiektu.

*Wprowadź*\
Typ obiektu, dla którego jest przypisywany magazyn.

## <a name="remarks"></a>Uwagi

Klasa opisuje iterator danych wyjściowych, który konstruuje obiekty typu `Type` w sekwencji, która generuje. Obiekt klasy `raw_storage_iterator` \< **ForwardIterator**, **Type**> uzyskuje dostęp do magazynu przez obiekt iteratora do przodu, klasy `ForwardIterator` , która jest określana podczas konstruowania obiektu. W przypadku obiektu najpierw klasy `ForwardIterator` wyrażenie ** & \* najpierw** musi wyznaczyć nieskonstruowany magazyn dla następnego obiektu (typu `Type` ) w wygenerowanej sekwencji.

Ta klasa adaptacji jest używana, gdy konieczne jest oddzielenie alokacji pamięci i konstruowania obiektów. `raw_storage_iterator`Może służyć do kopiowania obiektów do niezainicjowanego magazynu, na przykład pamięci przydzielonej za pomocą `malloc` funkcji.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Tworzy iterator nieprzetworzonego magazynu z określonym podstawowym iteratorem wyjściowym.|

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[element_type](#element_type)|Zapewnia typ, który opisuje element, który ma być przechowywany iterator magazynu RAW.|
|[iter_type](#iter_type)|Zapewnia typ, który opisuje iterator, który jest niezależnym iteratorem magazynu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[zakład](#op_star)|Operator dereferencji używany do implementowania wyrażenia iteratora danych wyjściowych \* `ii`  =  `x` .|
|[operator =](#op_eq)|Operator przypisania używany do implementowania wyrażenia iteratora nieprzetworzonego magazynu \* `i`  =  `x` na potrzeby przechowywania w pamięci.|
|[operator + +](#op_add_add)|Operatory przedrastające i postinkrementacji dla iteratorów nieprzetworzonych magazynów.|

### <a name="element_type"></a><a name="element_type"></a> element_type

Zapewnia typ, który opisuje element, który ma być przechowywany iterator magazynu RAW.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu klasy raw_storage_iterator `Type` .

### <a name="iter_type"></a><a name="iter_type"></a> iter_type

Zapewnia typ, który opisuje iterator, który jest niezależnym iteratorem magazynu.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `ForwardIterator` .

### <a name="operator"></a><a name="op_star"></a> zakład\*

Operator dereferencji używany do implementowania wyrażenia iteratora nieprzetworzonego magazynu o wielkości \* *II*  =  *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do iteratora nieprzetworzonego magazynu

#### <a name="remarks"></a>Uwagi

Wymagania dla a są wymagane przez `ForwardIterator` iterator nieprzetworzonego magazynu, które wymagają, aby tylko wyrażenie \* *II*  =  *t* było prawidłowe i nie zachodził o **`operator`** ani `operator=` na siebie. Operatory elementów członkowskich w tej implementacji zwracają ** \* to**, więc [operator =](#op_eq)(**consttype**&) może przepełnić rzeczywisty magazyn w wyrażeniu, takim jak \* *PTR*  =  `val` .

#### <a name="example"></a>Przykład

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
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_eq"></a> operator =

Operator przypisania używany do implementowania wyrażenia iteratora nieprzetworzonego magazynu \* *i*  =  *x* do przechowywania w pamięci.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość obiektu typu `Type` do wstawienia do pamięci.

#### <a name="return-value"></a>Wartość zwracana

Operator wstawia `val` do pamięci, a następnie zwraca odwołanie do iteratora nieprzetworzonego magazynu.

#### <a name="remarks"></a>Uwagi

Wymagania dotyczące `ForwardIterator` stanu, który musi spełniać iterator nieprzetworzonego magazynu, wymagają, aby tylko wyrażenie \* *II*  =  *t* było prawidłowe i nie zachodził niczego o **`operator`** ani `operator=` we własnym zakresie. Te operatory elementów członkowskich zwracają **`*this`** .

Operator przypisania konstruuje następny obiekt w sekwencji danych wyjściowych przy użyciu wartości iteratora przechowywanego `first` , oceniając nowe wyrażenie umieszczania `new ( (void*) & *first ) Type( val )` .

#### <a name="example"></a>Przykład

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
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="operator"></a><a name="op_add_add"></a> operator + +

Operatory przedrastające i postinkrementacji dla iteratorów nieprzetworzonych magazynów.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>Wartość zwracana

Iterator magazynu Raw lub odwołanie do iteratora nieprzetworzonego magazynu.

#### <a name="remarks"></a>Uwagi

Pierwszy operator ostatecznie próbuje wyodrębnić i przechowywać obiekt typu `CharType` ze skojarzonego strumienia wejściowego. Drugi operator wykonuje kopię obiektu, zwiększa obiekt, a następnie zwraca kopię.

Pierwszy operator przyrostu przyrostowego zwiększa przechowywany obiekt iteratora wyjściowego, a następnie zwraca ** \* tę**wartość.

Drugi operator postinkrementacji wykonuje kopię ** \* tego**elementu, zwiększa wartość przechowywanego obiektu iteratora wyjściowego, a następnie zwraca kopię.

Konstruktor przechowuje `first` jako obiekt iteratora danych wyjściowych.

#### <a name="example"></a>Przykład

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
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a><a name="raw_storage_iterator"></a> raw_storage_iterator

Tworzy iterator nieprzetworzonego magazynu z określonym podstawowym iteratorem wyjściowym.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator do przodu, który jest podstawą `raw_storage_iterator` konstruowanego obiektu.

#### <a name="example"></a>Przykład

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
```

```Output
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
```
