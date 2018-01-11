---
title: "tuple_size — klasa; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs: C++
helpviewer_keywords: std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef3d1fae353de8962684b080c223bd4a6a235acf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tuplesize-class"></a>tuple_size — klasa;
Liczba elementów raportów który `tuple` zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```  
// TEMPLATE STRUCT tuple_size  
template <class Tuple>  
   struct tuple_size;  
  
// number of elements in array  
template <class Elem, size_t Size>  
   struct tuple_size<array<Elem, Size>>  
      : integral_constant<size_t, Size>; 
  
// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>> 
      : integral_constant<size_t, 2>

// size of tuple  
template <class... Types>  
   struct tuple_size<tuple<Types...>>  
      : integral_constant<size_t, sizeof...(Types)>;  
  
// size of const tuple  
template <class Tuple>  
   struct tuple_size<const Tuple>;  
  
// size of volatile tuple  
template <class Tuple>  
   struct tuple_size<volatile Tuple>;  
  
// size of const volatile tuple  
template <class Tuple>  
   struct tuple_size<const volatile Tuple>;   
```  
  
#### <a name="parameters"></a>Parametry  
*Krotki*  
Typ spójnej kolekcji. 
  
*Element*  
Typ elementów tablicy. 
  
*Rozmiar*  
Rozmiar tablicy. 
  
*T1*  
Typ pierwszego elementu członkowskiego pary. 
  
*T2*  
Typ drugiego elementu członkowskiego pary. 
  
*Typy*  
Typy elementów spójnej kolekcji. 
  
  
## <a name="remarks"></a>Uwagi  
Szablon klasy ma element członkowski `value` będący wyrażeniem stałej całkowitej którego wartość jest zakres typu krotki `Tuple`.  
  
Specjalizacja szablonów dla tablic ma element członkowski `value` czyli wyrażeniu dającym stałą o wartości `Size`, która jest rozmiar tablicy.  
  
Specjalizacja szablonu dla pary ma element członkowski `value` będący wyrażeniem stałej całkowitej którego wartość jest równa 2.  
  
## <a name="example"></a>Przykład  
  
```cpp  
#include <tuple>   
#include <iostream>  
  
using namespace std;  
  
typedef tuple<int, double, int, double> MyTuple;  
int main()  
{  
    MyTuple c0(0, 1.5, 2, 3.7);  
  
    // display contents " 0 1 2 3"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0);  
    cout << " " << get<2>(c0);  
    cout << " " << get<3>(c0) << endl;  
  
    // display size " 4"   
    cout << " " << tuple_size<MyTuple>::value << endl;  
}  
```  
  
```Output  
 0 1.5 2 3.7  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<krotki >  
 **Nagłówek:** \<tablicy > (dla specjalizacji tablicy)  
 **Nagłówek:** \<narzędzie > (dla specjalizacji pary)  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<Tuple >](../standard-library/tuple.md)   
 [krotki](../standard-library/tuple-class.md)  
 [tuple_element — klasa](../standard-library/tuple-element-class-tuple.md)
