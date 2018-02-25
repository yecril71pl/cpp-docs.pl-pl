---
title: "not_equal_to — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xfunctional/std::not_equal_to
dev_langs:
- C++
helpviewer_keywords:
- not_equal_to function
- not_equal_to struct
ms.assetid: 333fce09-4f51-44e0-ba26-533bccffd485
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b456a53c47070ae44ff5a6ac1a676a0f2d211bdc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="notequalto-struct"></a>not_equal_to — Struktura
Predykat binarny, który wykonuje operacje nierówności ( `operator!=`) na jego argumenty.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Type = void>
struct not_equal_to : public binary_function<Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator!=
template <>
struct not_equal_to<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) != std::forward<U>(Right));
};
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Dowolnego typu, który obsługuje `operator!=` pobierającej argumentów operacji typu określonego lub wywnioskowany.  
  
 `Left`  
 Lewy operand operacji nierówności. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `T`.  
  
 `Right`  
 Prawy argument operacji nierówności. Szablon klasy niespecjalizowanej przyjmuje argument odwołania l-wartością typu `Type`. Specjalne szablonu doskonała przekazującej lewostronnie i argumenty odwołanie do r-wartości wywnioskować typu `U`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik `Left != Right`. Specjalne szablonu doskonała przekazywanie wynik, który ma typ zwracany przez `operator!=`.  
  
## <a name="remarks"></a>Uwagi  
 Obiekty typu `Type` musi umożliwiać porównywanie równości. Takie rozwiązanie wymaga `operator!=` zdefiniowane na zestaw obiektów spełnia właściwości matematyczne równoważność relacji. Wszystkie typy wbudowane liczbowych i wskaźnik spełnienia tego wymagania.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// functional_not_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 (6);  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),   
      not_equal_to<double>( ) );  
  
   cout << "The result of the element-wise not_equal_to comparsion\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
/* Output:  
The vector v1 = ( 0 1 4 5 8 9 )  
The vector v2 = ( -0 1 -4 5 -8 9 )  
The result of the element-wise not_equal_to comparsion  
between v1 & v2 is: ( 0 0 1 0 1 0 )  
*/  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<funkcjonalności >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



