---
title: '&lt;Wektor&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
dev_langs:
- C++
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: 297fb5bf602d8cc7d2f90e66fbb47dd433e90b86
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ltvectorgt-operators"></a>&lt;Wektor&gt; operatory
||||  
|-|-|-|  
|[operator!=](#op_neq)|[Operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[Operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator! =  
 Testy, jeśli obiekt po lewej stronie operatora nie jest taki sam jak obiekt po prawej stronie.  
  
```  
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** wektory nie są równe; **false** Jeśli wektory są takie same.  
  
### <a name="remarks"></a>Uwagi  
 Dwa wektory są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_ne.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
     v2.push_back( 2 );  
  
   if ( v1 != v2 )  
      cout << "Vectors not equal." << endl;  
   else  
      cout << "Vectors equal." << endl;  
}  
```  
  
```Output  
Vectors not equal.  
```  
  
##  <a name="op_lt"></a>  Operator&lt;  
 Testy, jeśli obiekt po lewej stronie operatora jest mniejsza niż obiekt po prawej stronie.  
  
```  
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wektora po lewej stronie operatora jest mniejsza niż wektora po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_lt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 < v2 )  
      cout << "Vector v1 is less than vector v2." << endl;  
   else  
      cout << "Vector v1 is not less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than vector v2.  
```  
  
##  <a name="op_lt_eq"></a>  Operator&lt;=  
 Testy, jeśli obiekt po lewej stronie operatora jest mniejsza lub równa obiektu po prawej stronie.  
  
```  
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wektora po lewej stronie operatora jest mniejsza niż lub równa wektora po prawej stronie operatora, w przeciwnym **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_le.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 <= v2 )  
      cout << "Vector v1 is less than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than or equal to vector v2.  
```  
  
##  <a name="op_eq_eq"></a>  operator ==  
 Testy, jeśli obiekt po lewej stronie operatora jest taki sam jak obiekt po prawej stronie.  
  
```  
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** w przypadku wektora po lewej stronie operatora równa wektora po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Dwa wektory są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v2.push_back( 1 );  
  
   if ( v1 == v2 )  
      cout << "Vectors equal." << endl;  
   else  
      cout << "Vectors not equal." << endl;  
}  
```  
  
```Output  
Vectors equal.  
```  
  
##  <a name="op_gt"></a>  Operator&gt;  
 Testy, jeśli obiekt po lewej stronie operatora jest większy niż obiekt po prawej stronie.  
  
```  
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wektor po lewej stronie operatora jest większa niż wektora po prawej stronie operatora; w przeciwnym razie **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_gt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
   v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 > v2 )  
      cout << "Vector v1 is greater than vector v2." << endl;  
   else  
      cout << "Vector v1 is not greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than vector v2.  
```  
  
##  <a name="op_gt_eq"></a>  Operator&gt;=  
 Testy, jeśli obiekt po lewej stronie operatora jest większa niż lub równa obiektu po prawej stronie.  
  
```  
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Obiekt typu **wektor**.  
  
 `right`  
 Obiekt typu **wektor**.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli wektor po lewej stronie operatora jest większa niż lub równa wektora po prawej stronie wektora, w przeciwnym **false**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// vector_op_ge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
     v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 >= v2 )  
      cout << "Vector v1 is greater than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than or equal to vector v2.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Wektor >](../standard-library/vector.md)

