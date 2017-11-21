---
title: '&lt;Lista&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
dev_langs: C++
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
caps.latest.revision: "7"
manager: ghogen
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: f3834fcb728d8faf0a2148a5a0c9449fef7e41c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltlistgt-operators"></a>&lt;Lista&gt; operatory
||||  
|-|-|-|  
|[operator! =](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator! =  
 Testy, jeśli obiekt listy po lewej stronie operatora nie jest taki sam jak obiekt listy po prawej stronie.  
  
```
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** list nie są równe; **false** listy są równe.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Dwie listy są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_ne.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
list <int> c1, c2;  
c1.push_back( 1 );  
c2.push_back( 2 );  
  
if ( c1 != c2 )  
cout << "Lists not equal." << endl;  
else  
cout << "Lists equal." << endl;  
}  
\* Output:  
Lists not equal.  
*\  
```  
  
##  <a name="op_lt"></a>operator&lt;  
 Testy, jeśli obiekt listy po lewej stronie operatora jest mniejsza niż obiekt listy po prawej stronie.  
  
```
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista po lewej stronie operatora jest mniejsza niż, ale nie równa liście po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Less — niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_lt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 < c2 )  
      cout << "List c1 is less than list c2." << endl;  
   else  
      cout << "List c1 is not less than list c2." << endl;  
}  
\* Output:   
List c1 is less than list c2.  
*\   
```  
  
##  <a name="op_lt_eq"></a>operator&lt;=  
 Testy, jeśli obiekt listy po lewej stronie operatora jest mniejsza niż lub równe obiekt listy po prawej stronie.  
  
```
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista po lewej stronie operatora jest mniejsza niż lub równa liście po prawej stronie operatora, w przeciwnym **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Mniejsze niż lub równe do relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_le.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 <= c2 )  
      cout << "List c1 is less than or equal to list c2." << endl;  
   else  
      cout << "List c1 is greater than list c2." << endl;  
}  
\* Output:   
List c1 is less than or equal to list c2.  
*\  
```  
  
##  <a name="op_eq_eq"></a>operator ==  
 Testy, jeśli obiekt listy po lewej stronie operatora jest taki sam jak obiekt listy po prawej stronie.  
  
```
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista po lewej stronie operatora jest równa liście po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Dwie listy są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_eq.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
  
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c2.push_back( 1 );  
  
   if ( c1 == c2 )  
      cout << "The lists are equal." << endl;  
   else  
      cout << "The lists are not equal." << endl;  
}  
\* Output:   
The lists are equal.  
*\  
```  
  
##  <a name="op_gt"></a>operator&gt;  
 Testy, jeśli obiekt listy po lewej stronie operatora jest większy niż obiekt listy po prawej stronie.  
  
```
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista po lewej stronie operatora jest większa niż liście po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Większa-niż relacji między dwoma obiektami jest oparta na porównanie pierwszego pary nierówne elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_gt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 > c2 )  
      cout << "List c1 is greater than list c2." << endl;  
   else  
      cout << "List c1 is not greater than list c2." << endl;  
}  
\* Output:   
List c1 is greater than list c2.  
*\  
```  
  
##  <a name="op_gt_eq"></a>operator&gt;=  
 Testy, jeśli obiekt listy po lewej stronie operatora jest większa niż lub równa obiekt listy po prawej stronie.  
  
```
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **listy**.  
  
 `right`  
 Obiekt typu **listy**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli lista po lewej stronie operatora jest większa niż lub równa liście po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie listę obiektów jest oparta na parowania porównanie ich elementów. Większa niż lub równa relacji między dwoma obiektami opiera się na porównanie pierwszego pary nierówne elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// list_op_ge.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 >= c2 )  
      cout << "List c1 is greater than or equal to list c2." << endl;  
   else  
      cout << "List c1 is less than list c2." << endl;  
}  
\* Output:   
List c1 is greater than or equal to list c2.  
*\  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<listy >](../standard-library/list.md)



