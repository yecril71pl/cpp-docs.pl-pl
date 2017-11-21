---
title: '&lt;Iterator&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xutility/std::operator!=
- xutility/std::operator&gt;
- xutility/std::operator&gt;=
- xutility/std::operator&lt;
- xutility/std::operator&lt;=
- xutility/std::operator+
- xutility/std::operator-
- xutility/std::operator==
dev_langs: C++
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
caps.latest.revision: "10"
manager: ghogen
helpviewer_keywords:
- std::operator!= (iterator)
- std::operator&gt; (iterator)
- std::operator&gt;= (iterator)
- std::operator&lt; (iterator)
- std::operator&lt;= (iterator), std::operator== (iterator)
ms.openlocfilehash: a6e5d30b970c3887c9ac7641ec39275acd9cd79d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltiteratorgt-operators"></a>&lt;Iterator&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator +](#op_add)|  
|[operator-](#operator-)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator! =  
 Testuje, czy obiekt iteratora po lewej stronie operatora nie jest równy obiektowi iteratora po prawej stronie.  
  
```  
template <class RandomIterator>  
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **iterator**.  
  
 `right`  
 Obiekt typu **iterator**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** obiekty iterator nie są równe; **false** iteratora obiekty są równe.  
  
### <a name="remarks"></a>Uwagi  
 Jeden z obiektów iteratora jest równa innej, jeśli odnoszą się do tych samych elementów w kontenerze. Jeśli punkt Iteratory dwóch różnych elementów w kontenerze, następnie nie są takie same.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_ne.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 9 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 4 5 6 7 8 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 8.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 7.  
The iterators are not equal.  
```  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testuje, czy obiekt iteratora po lewej stronie operatora jest równy obiektowi iteratora po prawej stronie.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,  
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,  
    const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu iteratora.  
  
 `right`  
 Obiekt typu iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli iteratora obiekty są równe; `false` obiekty iterator nie są równe.  
  
### <a name="remarks"></a>Uwagi  
 Jeden z obiektów iteratora jest równa innej, jeśli odnoszą się do tych samych elementów w kontenerze. Jeśli punkt Iteratory dwóch różnych elementów w kontenerze, następnie nie są takie same.  
  
 Pierwszy operatory dwóch szablonu zwrócić wartość true, tylko jeśli obie `left` i `right` przechowywania tego samego iteratora. Trzeci operator szablonu zwraca wartość true tylko wtedy, gdy oba `left` i `right` przechowywania tego samego strumienia wskaźnika. Zwraca czwarte operator szablonu ` left.equal ( right)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_eq.cpp  
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
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterators are not equal.  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż obiekt iteratora po prawej stronie.  
  
```  
template <class RandomIterator>  
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **iterator**.  
  
 `right`  
 Obiekt typu **iterator**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli iteratora po lewej stronie wyrażenia jest mniejsza niż iteratora po prawej stronie wyrażenia. **false** Jeśli jest większa niż lub równa iteratora po prawej stronie.  
  
### <a name="remarks"></a>Uwagi  
 Jeden obiekt iteratora jest mniejsza niż innym, jeśli dotyczy on elementu, która występuje wcześniej w kontenerze od elementu adresowane przez inny obiekt iteratora. Jeden obiekt iterator nie jest mniejsza niż innego Jeśli on dotyczy tego samego elementu jako obiektu iterator lub element później w kontenerze od elementu adresowane przez inny obiekt iteratora.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_lt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 0 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1& rVPOS2 initially point to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1& rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is not less than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Testuje, czy obiekt iteratora po lewej stronie operatora jest mniejszy niż lub równy obiektowi iteratora po prawej stronie.  
  
```  
template <class RandomIterator>  
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu iteratora.  
  
 `right`  
 Obiekt typu iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli iteratora po lewej stronie wyrażenia jest mniejsza niż lub równa iteratora po prawej stronie wyrażenia. **false** Jeśli jest większy niż iteratora po prawej stronie.  
  
### <a name="remarks"></a>Uwagi  
 Jeden obiekt iteratora jest mniejsza lub równa innej, jeśli jego dotyczy tego samego elementu lub elementu, która występuje wcześniej w kontenerze od elementu przywoływane przez inny obiekt iteratora. Jeden obiekt iteratora jest większa niż innym, jeśli spełnia element później w kontenerze od elementu adresowane przez inny obiekt iteratora.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_le.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS2 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż obiekt iteratora po prawej stronie.  
  
```  
template <class RandomIterator>  
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu iteratora.  
  
 `right`  
 Obiekt typu iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli iteratora po lewej stronie wyrażenia jest większa niż iteratora po prawej stronie wyrażenia. **false** Jeśli jest ona mniejsza niż iteratora po prawej stronie.  
  
### <a name="remarks"></a>Uwagi  
 Jeden obiekt iteratora jest większa niż innym, jeśli spełnia element później w kontenerze od elementu adresowane przez inny obiekt iteratora. Jeden obiekt iterator nie jest większa niż innego go dotyczy tego samego elementu jako obiektu iterator lub elementu, która występuje wcześniej w kontenerze od elementu adresowane przez inny obiekt iteratora.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_gt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Testuje, czy obiekt iteratora po lewej stronie operatora jest większy niż lub równy obiektowi iteratora po prawej stronie.  
  
```  
template <class RandomIterator>  
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu iteratora.  
  
 `right`  
 Obiekt typu iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli iteratora po lewej stronie wyrażenia jest większa niż lub równa iteratora po prawej stronie wyrażenia. **false** Jeśli jest mniejszy niż iteratora po prawej stronie.  
  
### <a name="remarks"></a>Uwagi  
 Jeden obiekt iteratora jest większa lub równa innej, jeśli jego dotyczy tego samego elementu lub element, który występuje później w kontenerze od elementu adresowane przez inny obiekt iteratora. Jeden obiekt iteratora jest mniejsza niż innym, jeśli dotyczy on elementu, która występuje wcześniej w kontenerze od elementu adresowane przez inny obiekt iteratora.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_ge.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( ) + 1;  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_add"></a>operator +  
 Dodaje przesunięcia do iteratora i zwraca `move_iterator` lub `reverse_iterator` adresowania wstawiony element w nowe położenie przesunięcia.  
  
```  
template <class RandomIterator, class Diff>  
move_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>  
reverse_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Liczba pozycji, const move_iterator — lub const reverse_iterator ma przesunięcia.  
  
 `right`  
 Iterator do przesunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca sumę `right`  +  `_Off`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   vector<int>::difference_type diff = 4;  
   rVPOS1 = diff +rVPOS1;  
  
   cout << "The iterator rVPOS1 now points to the fifth "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 now points to the fifth element  
 in the reversed sequence: 2.  
```  
  
##  <a name="operator-"></a>operator-  
 Odejmuje jeden iterator od innego i zwraca różnicę.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Iteratora.  
  
 `right`  
 Iteratora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różnica między dwoma Iteratory`.`  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy operator szablonu `left.base() - right.base()`.  
  
 Drugi operator szablonu zwraca `right.current - left.current`.  
  
 `Tdiff`jest określana przez typ zwracane wyrażenie. W przeciwnym razie jest `RandomIterator1::difference_type`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iterator_op_sub.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
          rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
        << "the first element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   for (i = 1; i < 5; ++i)    
   {  
      rVPOS2++;  
   }  
   cout << "The iterator rVPOS2 now points to the fifth "  
        << "element\n in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
  
   vector<int>::difference_type diff = rVPOS2 - rVPOS1;  
   cout << "The difference: rVPOS2 - rVPOS1= "  
        << diff << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 now points to the fifth element  
 in the reversed sequence: 2.  
The difference: rVPOS2 - rVPOS1= 4.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)

