---
title: "binary_negate — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::binary_negate
dev_langs: C++
helpviewer_keywords: binary_negate class
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5350576ec1b42620aa89f7fa48980e8227e13a80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="binarynegate-class"></a>binary_negate — Klasa
Klasy szablonów zapewnianie funkcji członkowskiej, która Negacja zwracana wartość określona funkcja binarnej.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Operation>
class binary_negate
    : public binaryFunction <typename Operation::first_argument_type,
                              typename Operation::second_argument_type, bool>
{
public:    
    explicit binary_negate(const Operation& Func);
    bool operator()(const typename Operation::first_argument_type& left,
                    const typename Operation::second_argument_type& right) const;
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Func`  
 Binarny funkcję, która ma być zanegowane.  
  
 `left`  
 Lewy argument operacji binarnego funkcję, która ma być zanegowane.  
  
 `right`  
 Prawy argument operacji binarnego funkcję, która ma być zanegowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Negacja funkcja binarnej.  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonu przechowuje kopię _ obiektu binarnego funkcja *Func*. Definiuje jego funkcji członkowskiej `operator()` jako zwracanie **!**\_ *FUNC (w lewo, prawo).*  
  
 Konstruktor obiektu `binary_negate` jest rzadko używana bezpośrednio. Funkcja Pomocnika [not2 —](../standard-library/functional-functions.md#not2) jest zwykle preferowany nad deklarowanie i użycie **binary_negator** predykatu karty.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// functional_binary_negate.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <unsigned int> v1;  
   vector <unsigned int>::iterator Iter1;  
  
   unsigned int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   unsigned int randVal = 0;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      rand_s(&randVal);  
      v1.push_back( randVal );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<unsigned int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,  
   // use the binary_negate function  
   sort( v1.begin( ), v1.end( ),  
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );  
  
   // The helper function not2 could also have been used  
   // in the above line and is usually preferred for convenience  
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );  
  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
\* Output:   
Original vector v1 = ( 6262 6262 2233879413 2621500314 580942933 3715465425 3739828298 )  
Sorted vector v1 = ( 6262 6262 580942933 2233879413 2621500314 3715465425 3739828298 )  
Resorted vector v1 = ( 3739828298 3715465425 2621500314 2233879413 580942933 6262 6262 )  
*\  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Odwołanie do biblioteki C++ Standard](../standard-library/cpp-standard-library-reference.md)



