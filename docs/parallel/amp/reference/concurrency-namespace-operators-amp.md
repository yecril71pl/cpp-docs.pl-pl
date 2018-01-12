---
title: "Operatory przestrzeń nazw współbieżności (AMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb0682a246cc2cd2acd8f22228fd25c99755f1cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-namespace-operators-amp"></a>Operatory przestrzeń nazw współbieżności (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[% — operator](#operator_mod)|[operator *](#operator_star)|  
|[operator +](#operator_add)|[operator-](#operator-)|[operator /](#operator_div)|  
|[operator ==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>operator ==   
 Określa, czy określone argumenty są takie same.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Jeden krotek do porównania.  
  
 `_Rhs`  
 Jeden krotek do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli krotki są takie same; w przeciwnym razie `false`.  
  
##  <a name="operator_neq"></a>operator! =   
 Określa, czy określone argumenty nie są takie same.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Jeden krotek do porównania.  
  
 `_Rhs`  
 Jeden krotek do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`krotki nie są równe; w przeciwnym razie `false`.  
  
##  <a name="operator_add"></a>operator +   

 Oblicza sumę component-wise określonych argumentów.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Jeden z argumentów do dodania.  
  
 `_Rhs`  
 Jeden z argumentów do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Suma component-wise określonych argumentów.  
  
##  <a name="operator-"></a>operator-   

 Oblicza component-wise różnica między określonymi argumentami.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Argument jest odejmowana od.  
  
 `_Rhs`  
 Argument do odjęcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Component-wise różnica między określonymi argumentami.  
  
##  <a name="operator_star"></a>operator *   

 Oblicza iloczyn component-wise określonych argumentów.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Jeden krotek, aby pomnożyć.  
  
 `_Rhs`  
 Jeden krotek, aby pomnożyć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Component-wise produktu określonych argumentów.  
  

##  <a name="operator_div"></a>operator /   
 Oblicza iloraz component-wise określonych argumentów.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Spójna kolekcja podział.  
  
 `_Rhs`  
 Spójna kolekcja znajdująca się próba podzielenia przez.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iloraz component-wise określonych argumentów.  
  
##  <a name="operator_mod"></a>% — operator   

 Oblicza resztę pierwszy argument określony przez drugi określonego argumentu.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rank`  
 Ranga argumentów spójnej kolekcji.  
  
 `_Lhs`  
 Spójną kolekcję na podstawie której jest obliczany modulo.  
  
 `_Rhs`  
 Spójna kolekcja znajdująca się na modulo przez.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik pierwszy modulo określony argument drugi argument określony.  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace współbieżności](concurrency-namespace-cpp-amp.md)
