---
title: "Współbieżność — przestrzeń nazwy operatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs: C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54c37f3262c6750bad4330780a4db09f2eef9d49
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-namespace-operators"></a>Współbieżność — przestrzeń nazwy podmiotów
||||  
|-|-|-|  
|[operator! =](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|  
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|  
|[operator ==](#operator_eq_eq)|[— operator||](#operator_lor)|  
  
##  <a name="operator_lor"></a>Operator &#124; &#124; Operator  
 Tworzy zadanie, które zostanie zakończony pomyślnie, jeśli jedno z zadań dostarczony jako argumenty zakończy się pomyślnie.  
  
```  
template<typename ReturnType>  
task<ReturnType> operator||(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void> operator||(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `ReturnType`  
 Typ zwrócony zadań.  
  
 `lhs`  
 Pierwszym zadaniem do łączenia w zadaniu wynikowym.  
  
 `rhs`  
 Drugie zadanie do łączenia w zadaniu wynikowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie kończące pomyślnie, gdy albo wejściowych zadań została ukończona pomyślnie. W przypadku wprowadzania zadania typu `T`, dane wyjściowe z tej funkcji będą `task<std::vector<T>`. W przypadku wprowadzania zadania typu `void` dane wyjściowe zadania zostanie również `task<void>`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli oba zadania zostały anulowane lub zgłaszają wyjątki zwrócony zadań zakończy się w stanie anulowane i jeden z wyjątków, jeśli żadnego nie zostaną napotkane, będą zgłaszane po wywołaniu `get()` lub `wait()` dla tego zadania.  
  
##  <a name="operator_amp_amp"></a>operator&amp; &amp; — Operator  
 Tworzy zadanie, które zostanie zakończony pomyślnie, gdy oba zadania podana jako argumenty pomyślnie ukończona.  
  
```  
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void>  operator&&(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `ReturnType`  
 Typ zwrócony zadań.  
  
 `lhs`  
 Pierwszym zadaniem do łączenia w zadaniu wynikowym.  
  
 `rhs`  
 Drugie zadanie do łączenia w zadaniu wynikowym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie, które zostanie wykonane pomyślnie, gdy oba wejściowych zadania zostały ukończone pomyślnie. W przypadku wprowadzania zadania typu `T`, dane wyjściowe z tej funkcji będą `task<std::vector<T>>`. W przypadku wprowadzania zadania typu `void` dane wyjściowe zadania zostanie również `task<void>`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jedno z zadań została anulowana lub zgłasza wyjątek, zadanie zwrócone ukończy wcześnie w stanie anulowane i, jeśli jest encoutered, zostanie wygenerowany wyjątek, jeśli wywołujesz `get()` lub `wait()` dla tego zadania.  
  
##  <a name="operator_eq_eq"></a>operator == — Operator  
 Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest równa `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych wektora po lewej stronie operatora jest równa równoczesnych wektora po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Dwa wektory równoczesnych są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
##  <a name="operator_neq"></a>operator! = — Operator  
 Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora nie jest równa `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wektory współbieżnych nie są równe; `false` równoczesnych wektory są równe.  
  
### <a name="remarks"></a>Uwagi  
 Dwa wektory równoczesnych są takie same, jeśli mają one taką samą liczbę elementów i ich odpowiednich elementy mają takie same wartości. W przeciwnym razie ich nie są równe.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
##  <a name="operator_lt"></a>operator&lt; — Operator  
 Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejsza niż `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych wektora po lewej stronie operatora jest mniejsza niż równoczesnych wektora po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zachowanie tego operatora jest taki sam jak równoważne operator `vector` klasy w `std` przestrzeni nazw.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
##  <a name="operator_lt_eq"></a>operator&lt;= — Operator  
 Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejsze niż lub równe `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych wektora po lewej stronie operatora jest mniejsza niż lub równe równoczesnych wektora po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zachowanie tego operatora jest taki sam jak równoważne operator `vector` klasy w `std` przestrzeni nazw.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
##  <a name="operator_gt"></a>operator&gt; — Operator  
 Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest większa niż `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych wektora po lewej stronie operatora jest większa niż równoczesnych wektora po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zachowanie tego operatora jest taki sam jak równoważne operator `vector` klasy w `std` przestrzeni nazw.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
##  <a name="operator_gt_eq"></a>operator&gt;= — Operator  
 Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest większa niż lub równa `concurrent_vector` obiektu po prawej stronie.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `A1`  
 Typ alokatora pierwszego `concurrent_vector` obiektu.  
  
 `A2`  
 Allocator — typ drugiego `concurrent_vector` obiektu.  
  
 `_A`  
 Obiekt typu `concurrent_vector`.  
  
 `_B`  
 Obiekt typu `concurrent_vector`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli równoczesnych wektor po lewej stronie operatora jest większa niż lub równa równoczesnych wektora po prawej stronie operatora; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Zachowanie tego operatora jest taki sam jak równoważne operator `vector` klasy w `std` przestrzeni nazw.  
  
 Ta metoda nie jest bezpieczną współbieżność w odniesieniu do innych metod, które można modyfikować albo wektorów równoczesnych `_A` lub `_B`.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
