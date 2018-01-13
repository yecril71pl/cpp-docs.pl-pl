---
title: "front_insert_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
dev_langs: C++
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 893d46e0f34bb86ce4e9d13fec4d3302282f2e00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="frontinsertiterator-class"></a>front_insert_iterator — Klasa
Opisuje adapter iteratora, który spełnia wymagania iteratora danych wyjściowych. Wstawia (a nie zastępuje) elementy do przedniego końca sekwencji i w ten sposób zapewnia semantykę, która różni się od semantyki zastępowania, dostarczanej przez iteratory kontenerów sekwencji C++. `front_insert_iterator` Klasy jest którego ma zastosowany szablon na typ kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Container>  
class front_insert_iterator;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Container`  
 Typ kontenera do przodu, z których mają zostać wstawione przez elementy `front_insert_iterator`.  
  
## <a name="remarks"></a>Uwagi  
 Kontener musi spełniać wymagania dla sekwencji wstawiania na przód, gdzie jest możliwe wstawianie elementów na początek sekwencji w amortyzowanym stałym czasie. Kontenery sekwencji standardowa biblioteka C++, zdefiniowane przez [deque — klasa](../standard-library/deque-class.md) i [list — klasa](../standard-library/list-class.md) Podaj wymagane `push_front` element członkowski funkcji i spełniają tych wymagań. Z kolei sekwencji kontenerów zdefiniowanych przez [vector — klasa](../standard-library/vector-class.md) nie spełniają tych wymagań i nie może być dostosowane do użycia z `front_insert_iterator`s. A `front_insert_iterator` zawsze musi zostać zainicjowany z jego kontenera.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[front_insert_iterator —](#front_insert_iterator)|Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[container_type](#container_type)|Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator *](#op_star)|Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` do przodu wstawiania.|  
|[operator ++](#op_add_add)|Zwiększa `front_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.|  
|[operator =](#op_eq)|Operator przypisania używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x` do przodu wstawiania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<iteratora >  
  
 **Namespace:** Standard  
  
##  <a name="container_type"></a>front_insert_iterator::container_type  
 Typ, który reprezentuje kontener, w którym ma być przeprowadzone wstawienie na przód.  
  
```  
typedef Container container_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **kontenera**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_container_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> >::container_type L2 = L1;  
   front_inserter ( L2 ) = 20;  
   front_inserter ( L2 ) = 10;  
   front_inserter ( L2 ) = 40;  
  
   list <int>::iterator vIter;  
   cout << "The list L2 is: ( ";  
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L2 is: ( 40 10 20 ).  
*\  
```  
  
##  <a name="front_insert_iterator"></a>front_insert_iterator::front_insert_iterator  
 Tworzy iterator, który może wstawić elementy z przodu określonego obiektu kontenera.  
  
```  
explicit front_insert_iterator(Container& _Cont);
```  
  
### <a name="parameters"></a>Parametry  
 `_Cont`  
 Obiekt kontenera, w którym `front_insert_iterator` jest, aby wstawić elementów.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `front_insert_iterator` dla parametru obiektu kontenera.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_front_insert_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for (i = -1 ; i < 9 ; ++i )    
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   // Using the member function to insert an element  
   front_inserter ( L ) = 20;  
  
   // Alternatively, one may use the template function  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="op_star"></a>front_insert_iterator::operator *  
 Wyłuskań iteratora insert zwracanie element, który spełnia.  
  
```  
front_insert_iterator<Container>& operator*();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja członkowska zwraca wartość elementu problemu.  
  
### <a name="remarks"></a>Uwagi  
 Używane do implementowania wyrażenia iteratora dane wyjściowe  **\*Iter** = **wartość**. Jeśli **Iter** jest iteratora, którego dotyczy elementu w sekwencji, następnie  **\*Iter** = **wartość** zamienia wartość tego elementu, a nie Zmień łączna liczba elementów w sekwencji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   list <int>::iterator L_Iter;  
  
   list<int> L;  
   for ( i = -1 ; i < 9 ; ++i )   
   {  
      L.push_back ( 2 * i );  
   }  
  
   cout << "The list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator< list < int> > Iter(L);  
 *Iter = 20;  
  
   // Alternatively, you may use  
   front_inserter ( L ) = 30;  
  
   cout << "After the front insertions, the list L is:\n ( ";  
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)  
      cout << *L_Iter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L is:  
 ( -2 0 2 4 6 8 10 12 14 16 ).  
After the front insertions, the list L is:  
 ( 30 20 -2 0 2 4 6 8 10 12 14 16 ).  
*\  
```  
  
##  <a name="op_add_add"></a>front_insert_iterator::operator ++  
 Zwiększa `back_insert_iterator` do następnej lokalizacji, w której może być przechowywana wartość.  
  
```  
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `front_insert_iterator` adresowania następnej lokalizacji, w której może być przechowywana wartość.  
  
### <a name="remarks"></a>Uwagi  
 Operatory zarówno preincrementation i postincrementation zwracać ten sam rezultat.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_op_incre.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="op_eq"></a>front_insert_iterator::operator =  
 Dołącza (wypchnięcia) wartość na początku kontenera.  
  
```  
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```  
  
### <a name="parameters"></a>Parametry  
 `val`  
 Wartość do przypisania do kontenera.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do ostatniego elementu wstawiony z przodu kontenera.  
  
### <a name="remarks"></a>Uwagi  
 Oblicza pierwszy operator członkowski `container.push_front( val)`, zwraca `*this`.  
  
 Oblicza drugi operator elementu członkowskiego  
  
 `container->push_front((typename Container::value_type&&) val)`,  
  
 Zwraca `*this`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L1;  
   front_insert_iterator<list<int> > iter ( L1 );  
 *iter = 10;  
   iter++;  
 *iter = 20;  
   iter++;  
 *iter = 30;  
   iter++;  
  
   list <int>::iterator vIter;  
   cout << "The list L1 is: ( ";  
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The list L1 is: ( 30 20 10 ).  
*\  
```  
  
##  <a name="reference"></a>front_insert_iterator::Reference  
 Typ, który zawiera odwołanie do elementu w sekwencji kontrolowanej przez skojarzony kontener.  
  
```  
typedef typename Container::reference reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp  
// front_insert_iterator_reference.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <list>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   list<int> L;  
   front_insert_iterator<list<int> > fiivIter( L );  
 *fiivIter = 10;  
 *fiivIter = 20;  
 *fiivIter = 30;  
  
   list<int>::iterator LIter;  
   cout << "The list L is: ( ";  
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)  
      cout << *LIter << " ";  
   cout << ")." << endl;  
  
   front_insert_iterator<list<int> >::reference   
        RefFirst = *(L.begin ( ));  
   cout << "The first element in the list L is: "   
        << RefFirst << "." << endl;  
}  
\* Output:   
The list L is: ( 30 20 10 ).  
The first element in the list L is: 30.  
*\  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

