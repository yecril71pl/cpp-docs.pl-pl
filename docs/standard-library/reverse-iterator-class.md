---
title: "reverse_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
dev_langs: C++
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 810f50a17dcdef3aac53462ac059a4aedd4343a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="reverseiterator-class"></a>reverse_iterator — Klasa
Klasa szablonu to adapter iteratora, opisujący obiekt odwróconego iteratora, który zachowuje się jak iterator dostępu swobodnego lub dwukierunkowy, tylko że w odwrotnej kolejności. Umożliwia przechodzenie do tyłu zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class RandomIterator>  
class reverse_iterator  
```  
  
#### <a name="parameters"></a>Parametry  
 RandomIterator  
 Typ reprezentujący iterator, który ma zostać dostosowany do pracy w odwrotnej kolejności.  
  
## <a name="remarks"></a>Uwagi  
 Również definiować istniejących kontenery standardowa biblioteka C++ `reverse_iterator` i `const_reverse_iterator` typy i funkcje Członkowskie `rbegin` i `rend` , które zwracają Iteratory odwrotnej. Te iteratory mają semantykę nadpisywania. `reverse_iterator` Karty uzupełniają tej funkcji, jak oferuje Wstaw semantykę i może również służyć strumieni.  
  
 `reverse_iterator` Wymagający iteratora dwukierunkowego nie mogą wywoływać żadnego elementu członkowskiego funkcji `operator+=`, `operator+`, `operator-=`, `operator-`, lub `operator[]`, która może być używana tylko z Iteratory dostępie swobodnym.  
  
 Zakres iteratora [*pierwszy*, *ostatniego*), gdzie nawias kwadratowy po lewej stronie wskazuje włączenia *pierwszy* i wskazuje nawias po prawej stronie Uwzględnianie elementów, ale nie więcej niż *ostatniego* samej siebie. Te same elementy znajdują się w kolejności odwróconej [ **rev** - *pierwszy*, **rev** - *ostatniego*), Jeśli *ostatniego* jest element co przeszłości —-end w sekwencji, następnie pierwszy element **rev** - *pierwszy* w kolejności odwróconej punktami \*(*ostatniego* - 1). Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:  
  
 &\*( **reverse_iterator** ( *i* )) == &\*( *i* - 1).  
  
 W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. W takim przypadku iteratora dotyczą element 6 w sekwencji, (2, 4, 6, 8), a następnie `reverse_iterator` będzie adresu elementu 4 w odwrotnej kolejności (8, 6, 4, 2).  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[reverse_iterator](#reverse_iterator)|Tworzy domyślny `reverse_iterator` lub `reverse_iterator` z iteratora podstawowej.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwiema `reverse_iterator`s odwołujących się do elementów w tym samym kontenerze.|  
|[iterator_type](#iterator_type)|Typ, który udostępnia podstawowe iteratora dla `reverse_iterator`.|  
|[wskaźnik](#pointer)|Typ, który dostarcza wskaźnik do elementu, który został opisany w `reverse_iterator`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu, który został opisany w `reverse_iterator`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Podstawa](#base)|Odzyskuje podstawowej iteratora z jego `reverse_iterator`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator_star](#op_star)|Zwraca element, który `reverse_iterator` adresów.|  
|[operator +](#op_add)|Dodaje przesunięcia do iteratora i zwraca nowy `reverse_iterator` adresowania wstawiony element w nowe położenie przesunięcia.|  
|[operator ++](#op_add_add)|Zwiększa `reverse_iterator` do następnego elementu.|  
|[+= — operator](#op_add_eq)|Dodaje określone przesunięcie z `reverse_iterator`.|  
|[operator-](#operator-)|Odejmuje przesunięcie od `reverse_iterator` i zwraca `reverse_iterator` adresowania elementu w położeniu przesunięcia.|  
|[operator--](#operator--)|Zmniejsza `reverse_iterator` do poprzedniego elementu.|  
|[operator-=](#operator-_eq)|Odejmuje określone przesunięcie z `reverse_iterator`.|  
|[operator ->](#operator-_gt)|Zwraca wskaźnik do elementu dotyczy `reverse_iterator`.|  
|[Operator &#91; &#93;](#op_at)|Zwraca odwołanie do przesunięcia element z elementu dotyczy `reverse_iterator` przez określoną liczbę pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
##  <a name="base"></a>reverse_iterator::Base  
 Odzyskuje podstawowej iteratora z jego `reverse_iterator`.  
  
```   
RandomIterator base() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator podstawowy `reverse_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Tożsamości, która dotyczy wszystkich Iteratory odwrotnej ich podstawowej Iteratory jest:  
  
 &\*( `reverse_iterator` ( *i* )) == &\*( *i* - 1).  
  
 W praktyce oznacza to, że w kolejności odwróconej `reverse_iterator` odnoszą się do elementu jedną pozycję poza (do prawej) element iteratora ma określone w oryginalnej sekwencji. W takim przypadku iteratora dotyczą element 6 w sekwencji, (2, 4, 6, 8), a następnie `reverse_iterator` będzie adresu elementu 4 w odwrotnej kolejności (8, 6, 4, 2).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_base.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::iterator pos, bpos;  
   pos = find ( vec.begin ( ), vec.end ( ), 6 );  
   cout << "The iterator pos points to: " << *pos << "." << endl;  
  
   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;  
  
   reverse_iterator<it_vec_int_type> rpos ( pos );  
   cout << "The reverse_iterator rpos points to: " << *rpos   
        << "." << endl;  
  
   bpos = rpos.base ( );  
   cout << "The iterator underlying rpos is bpos & it points to: "   
        << *bpos << "." << endl;  
}  
```  
  
##  <a name="difference_type"></a>reverse_iterator::difference_type  
 Typ, który zawiera różnicę między dwiema `reverse_iterator`s odwołujących się do elementów w tym samym kontenerze.  
  
```   
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type; 
```  
  
### <a name="remarks"></a>Uwagi  
 `reverse_iterator` Typu różnica jest taki sam jak typ różnica iteratora.  
  
 Typ jest synonimem typename cechy iteratora `iterator_traits` \< **RandomIterator**> **:: wskaźnika**.  
  
### <a name="example"></a>Przykład  
  Zobacz [reverse_iterator::operator &#91; &#93;](#op_at) przykład sposobu deklarowanie i użycie `difference_type`.  
  
##  <a name="iterator_type"></a>reverse_iterator::iterator_type  
 Typ, który udostępnia podstawowe iteratora dla `reverse_iterator`.  
  
```  
typedef RandomIterator iterator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu `Iterator`.  
  
### <a name="example"></a>Przykład  
  Zobacz [reverse_iterator::base](#base) przykład sposobu deklarowanie i użycie `iterator_type`.  
  
##  <a name="op_star"></a>reverse_iterator::operator *  
 Zwraca element, którego dotyczy reverse_iterator.  
  
```   
reference operator*() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość elementów wchodzących w reverse_iterator.  
  
### <a name="remarks"></a>Uwagi  
 Operator zwraca \*( **bieżącego** - 1).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_ref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::iterator pos, bpos;  
   pos = find ( vec.begin ( ), vec.end ( ), 6 );  
  
   // Declare a difference type for a parameter  
   // declare a reference return type  
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;  
   cout << "The iterator pos points to: " << refpos << "." << endl;  
}  
```  
  
##  <a name="op_add"></a>reverse_iterator::operator +  
 Dodaje przesunięcia do iteratora i zwraca nowy `reverse_iterator` adresowania wstawiony element w nowe położenie przesunięcia.  
  
```  
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Off`  
 Przesunięcia, które mają zostać dodane do wstecznego iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `reverse_iterator` adresowania element przesunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej można używać tylko w przypadku `reverse_iterator` spełnia wymagania dotyczące iteratora dostępie swobodnym.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_add.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the first element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added  
   cout << "After the +2 offset, the iterator rVPOS2 points\n"  
        << " to the 3rd element in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The vector vec reversed is: ( 10 8 6 4 2 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
After the +2 offset, the iterator rVPOS2 points  
 to the 3rd element in the reversed sequence: 6.  
```  
  
##  <a name="op_add_add"></a>reverse_iterator::operator ++  
 Zwiększa reverse_iterator do poprzedniego elementu.  
  
```  
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy operator zwraca preincremented `reverse_iterator` , a drugie postincrement operator kopię zwiększany `reverse_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej można używać tylko w przypadku `reverse_iterator` spełnia wymagania dotyczące iteratora dwukierunkowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i - 1 );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   rVPOS1++;  // postincrement, preincrement: ++rVPSO1  
  
   cout << "After incrementing, the iterator rVPOS1 points\n"  
        << " to the second element in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 3 5 7 9 ).  
The vector vec reversed is: ( 9 7 5 3 1 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 9.  
After incrementing, the iterator rVPOS1 points  
 to the second element in the reversed sequence: 7.  
```  
  
##  <a name="op_add_eq"></a>reverse_iterator::operator +=  
 Dodaje określone przesunięcie z reverse_iterator.  
  
```  
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```  
  
### <a name="parameters"></a>Parametry  
 `Off`  
 Przesunięcie, o którą należy zwiększyć iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu dotyczy `reverse_iterator`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_addoff.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )   
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   rVPOS1+=2;   // addition of an offset  
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"  
        << " to the third element in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The vector vec reversed is: ( 10 8 6 4 2 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
After the +2 offset, the iterator rVPOS1 now points  
 to the third element in the reversed sequence: 6.  
```  
  
##  <a name="reverse_iterator__operator-"></a>reverse_iterator::operator-  
 Odejmuje przesunięcie od `reverse_iterator` i zwraca `reverse_iterator` adresowania elementu w położeniu przesunięcia.  
  
```  
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Off`  
 Przesunięcie jest odejmowana od reverse_iterator.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `reverse_iterator` adresowania element przesunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej można używać tylko w przypadku `reverse_iterator` spełnia wymagania dotyczące iteratora dostępie swobodnym.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_sub.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 3 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the first element  
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;  
  
   cout << "The iterator rVPOS1 initially points to the last "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted  
   cout << "After the -2 offset, the iterator rVPOS2 points\n"  
        << " to the 2nd element from the last in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 3 6 9 12 15 ).  
The vector vec reversed is: ( 15 12 9 6 3 ).  
The iterator rVPOS1 initially points to the last element  
 in the reversed sequence: 3.  
After the -2 offset, the iterator rVPOS2 points  
 to the 2nd element from the last in the reversed sequence: 9.  
```  
  
##  <a name="reverse_iterator__operator--"></a>reverse_iterator::operator--  
 Zmniejsza reverse_iterator do poprzedniego elementu.  
  
```  
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy operator zwraca predecremented `reverse_iterator` , a drugie postdecrement operator kopię zmniejszany `reverse_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej można używać tylko w przypadku `reverse_iterator` spełnia wymagania dotyczące iteratora dwukierunkowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_decr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i - 1 );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the first element  
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;  
  
   cout << "The iterator rVPOS1 initially points to the last "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1  
  
   cout << "After the decrement, the iterator rVPOS1 points\n"  
        << " to the next-to-last element in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 3 5 7 9 ).  
The vector vec reversed is: ( 9 7 5 3 1 ).  
The iterator rVPOS1 initially points to the last element  
 in the reversed sequence: 1.  
After the decrement, the iterator rVPOS1 points  
 to the next-to-last element in the reversed sequence: 3.  
```  
  
##  <a name="reverse_iterator__operator-_eq"></a>reverse_iterator::operator-=  
 Odejmuje określone przesunięcie z `reverse_iterator`.  
  
```  
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```  
  
### <a name="parameters"></a>Parametry  
 `Off`  
 Przesunięcie jest odejmowana od `reverse_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej można używać tylko w przypadku `reverse_iterator` spełnia wymagania dotyczące iteratora dostępie swobodnym.  
  
 Operator ocenia **bieżącego** + _ *poza*. Zwraca  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_op_suboff.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 3 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the first element  
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;  
  
   cout << "The iterator rVPOS1 initially points to the last "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   rVPOS1-=2;      // Subtraction of an offset  
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"  
        << " to the 2nd element from the last in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 3 6 9 12 15 ).  
The vector vec reversed is: ( 15 12 9 6 3 ).  
The iterator rVPOS1 initially points to the last element  
 in the reversed sequence: 3.  
After the -2 offset, the iterator rVPOS1 now points  
 to the 2nd element from the last in the reversed sequence: 9.  
```  
  
##  <a name="reverse_iterator__operator-_gt"></a>reverse_iterator::operator-&gt;  
 Zwraca wskaźnik do elementu dotyczy `reverse_iterator`.  
  
```   
pointer operator->() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu dotyczy `reverse_iterator`.  
  
### <a name="remarks"></a>Uwagi  
 Operator zwraca  **& \* \*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_ptrto.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <utility>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef vector<pair<int,int> > pVector;  
   pVector vec;  
   vec.push_back(pVector::value_type(1,2));  
   vec.push_back(pVector::value_type(3,4));  
   vec.push_back(pVector::value_type(5,6));  
  
   pVector::iterator pvIter;  
   cout << "The vector vec of integer pairs is:\n( ";  
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)  
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";  
   cout << ")" << endl << endl;  
  
   pVector::reverse_iterator rpvIter;  
   cout << "The vector vec reversed is:\n( ";  
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )  
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";  
   cout << ")" << endl << endl;  
  
   pVector::iterator pos = vec.begin ( );  
   pos++;  
   cout << "The iterator pos points to:\n( " << pos -> first << ", "   
   << pos -> second << " )" << endl << endl;  
  
   pVector::reverse_iterator rpos (pos);   
  
   // Use operator -> with return type: why type int and not int*  
   int fint = rpos -> first;  
   int sint = rpos -> second;  
  
   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "   
   << sint << " )" << endl;  
}  
```  
  
```Output  
The vector vec of integer pairs is:  
( ( 1, 2) ( 3, 4) ( 5, 6) )  
  
The vector vec reversed is:  
( ( 5, 6) ( 3, 4) ( 1, 2) )  
  
The iterator pos points to:  
( 3, 4 )  
  
The reverse_iterator rpos points to:  
( 1, 2 )  
```  
  
##  <a name="op_at"></a>reverse_iterator::operator]  
 Zwraca odwołanie do przesunięcia element z elementu dotyczy `reverse_iterator` przez określoną liczbę pozycji.  
  
```   
reference operator[](difference_type Off) const;
```  
  
### <a name="parameters"></a>Parametry  
 `Off`  
 Przesunięcie od `reverse_iterator` adres.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu przesunięcie.  
  
### <a name="remarks"></a>Uwagi  
 Operator zwraca  **\*** (  **\*to** + `Off`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_ret_ref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::iterator pos;  
   pos = find ( vec.begin ( ), vec.end ( ), 8 );  
   reverse_iterator<vector<int>::iterator> rpos ( pos );  
  
   // Declare a difference type for a parameter  
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;  
  
   cout << "The iterator pos points to: " << *pos << "." << endl;  
   cout << "The iterator rpos points to: " << *rpos << "." << endl;  
  
   // Declare a reference return type & use operator[]  
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];  
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;     
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The vector vec reversed is: ( 10 8 6 4 2 ).  
The iterator pos points to: 8.  
The iterator rpos points to: 6.  
The iterator rpos now points to: 2.  
```  
  
##  <a name="pointer"></a>reverse_iterator::Pointer  
 Typ, który dostarcza wskaźnik do elementu, który został opisany w `reverse_iterator`.  
  
```  
typedef typename iterator_traits<RandomIterator>::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem typename cechy iteratora `iterator_traits` \< *RandomIterator*> **:: wskaźnika**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_pointer.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <utility>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef vector<pair<int,int> > pVector;  
   pVector vec;  
   vec.push_back( pVector::value_type( 1,2 ) );  
   vec.push_back( pVector::value_type( 3,4 ) );  
   vec.push_back( pVector::value_type( 5,6 ) );  
  
   pVector::iterator pvIter;  
   cout << "The vector vec of integer pairs is:\n" << "( ";  
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)  
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";  
   cout << ")" << endl;  
  
   pVector::reverse_iterator rpvIter;  
   cout << "\nThe vector vec reversed is:\n" << "( ";  
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)  
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";  
   cout << ")" << endl;  
  
   pVector::iterator pos = vec.begin ( );  
   pos++;  
   cout << "\nThe iterator pos points to:\n"  
        << "( " << pos -> first << ", "  
        << pos -> second << " )" << endl;  
  
   pVector::reverse_iterator rpos (pos);  
   cout << "\nThe iterator rpos points to:\n"  
        << "( " << rpos -> first << ", "  
        << rpos -> second << " )" << endl;  
}  
```  
  
```Output  
The vector vec of integer pairs is:  
( ( 1, 2) ( 3, 4) ( 5, 6) )  
  
The vector vec reversed is:  
( ( 5, 6) ( 3, 4) ( 1, 2) )  
  
The iterator pos points to:  
( 3, 4 )  
  
The iterator rpos points to:  
( 1, 2 )  
```  
  
##  <a name="reference"></a>reverse_iterator::Reference  
 Typ, który zawiera odwołanie do elementu, który został opisany w reverse_iterator.  
  
```  
typedef typename iterator_traits<RandomIterator>::reference reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem typename cechy iteratora `iterator_traits` \< *RandomIterator*> **:: odwołanie**.  
  
### <a name="example"></a>Przykład  
  Zobacz [reverse_iterator::operator &#91; &#93;](#op_at) lub [reverse_iterator::operator *](#op_star) przykłady deklarowanie i użycie **odwołania**.  
  
##  <a name="reverse_iterator"></a>reverse_iterator::reverse_iterator  
 Tworzy domyślny `reverse_iterator` lub `reverse_iterator` z iteratora podstawowej.  
  
```   
reverse_iterator();  
explicit reverse_iterator(RandomIterator right);

template <class Type>  
reverse_iterator(const reverse_iterator<Type>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Iterator, który ma być dostosowane do `reverse_iterator`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślnie `reverse_iterator` lub `reverse_iterator` adaptacja podstawowej iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Tożsamość, która odnosi wszystkie iteratory odwrócone do ich iteratorów podstawowych, to:  
  
 &\*( `reverse_iterator` ( *i* )) == &\*( *i* - 1).  
  
 W praktyce oznacza to, że w odwróconej sekwencji reverse_iterator będzie się odnosił do elementu w jednej pozycji poza elementem (z jego prawej strony), do którego odnosił się iterator w oryginalnej sekwencji. W takim przypadku iteratora dotyczą element 6 w sekwencji, (2, 4, 6, 8), a następnie `reverse_iterator` będzie adresu elementu 4 w odwrotnej kolejności (8, 6, 4, 2).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// reverse_iterator_reverse_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <algorithm>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rvIter;  
   cout << "The vector vec reversed is: ( ";  
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)  
      cout << *rvIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::iterator pos;  
   pos = find ( vec.begin ( ), vec.end ( ), 4 );  
   cout << "The iterator pos = " << *pos << "." << endl;  
  
   vector <int>::reverse_iterator rpos ( pos );  
   cout << "The reverse_iterator rpos = " << *rpos   
        << "." << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)

