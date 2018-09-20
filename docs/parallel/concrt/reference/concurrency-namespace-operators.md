---
title: Operatory przestrzeni nazw współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9eb820b533b74d5634695ddabda26f081a35f95
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436926"
---
# <a name="concurrency-namespace-operators"></a>Operatory przestrzeni nazw współbieżności

||||
|-|-|-|
|[operator!=](#operator_neq)|[Operator&amp;&amp;](#operator_amp_amp)|[Operator&gt;](#operator_gt)|
|[Operator&gt;=](#operator_gt_eq)|[Operator&lt;](#operator_lt)|[Operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[— operator||](#operator_lor)|

##  <a name="operator_lor"></a>  operator&#124; &#124; — Operator

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczone jako argumenty zakończą się pomyślnie.

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

*ReturnType*<br/>
Typ zwracanego zadania.

*Lewa strona reguły przepisywania*<br/>
Pierwsze zadanie do połączenia w zadanie wynikowe.

*RHS*<br/>
Drugie zadanie połączyć w zadanie wynikowe.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które zostaje wykonane pomyślnie, gdy jedno z zadań wejściowych została ukończona pomyślnie. Jeśli zadania wejściowe są typu `T`, danymi wyjściowymi tej funkcji będą `task<std::vector<T>`. Jeśli zadania wejściowe są typu `void` zadaniem wyjściowym też będzie `task<void>`.

### <a name="remarks"></a>Uwagi

Jeśli oba zadania zostały anulowane lub generują wyjątki, zwrócone zadanie zostanie ukończone ze stanem anulowane, a jeden z wyjątków, jeśli żadnego nie zostaną napotkane, zostanie zgłoszony podczas wywoływania `get()` lub `wait()` dla tego zadania.

##  <a name="operator_amp_amp"></a>  operator&amp; &amp; — Operator

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy oba zadania dostarczone jako argumenty zakończą się pomyślnie.

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

*ReturnType*<br/>
Typ zwracanego zadania.

*Lewa strona reguły przepisywania*<br/>
Pierwsze zadanie do połączenia w zadanie wynikowe.

*RHS*<br/>
Drugie zadanie połączyć w zadanie wynikowe.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które zostaje wykonane pomyślnie, gdy oba zadania wejściowe zostały ukończone pomyślnie. Jeśli zadania wejściowe są typu `T`, danymi wyjściowymi tej funkcji będą `task<std::vector<T>>`. Jeśli zadania wejściowe są typu `void` zadaniem wyjściowym też będzie `task<void>`.

### <a name="remarks"></a>Uwagi

Jeśli jedno z zadań zostanie anulowane lub zgłasza wyjątek, zwrócone zadanie zostanie ukończone przedwcześnie ze stanem anulowane, a wyjątek, jeśli wystąpi, zostanie zgłoszony, jeśli wywołujesz `get()` lub `wait()` dla tego zadania.

##  <a name="operator_eq_eq"></a>  operator == — Operator

Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest równy `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli współbieżnego wektora po lewej stronie operatora jest równy współbieżnego wektora po prawej stronie operatora; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Dwa wektory współbieżne są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

##  <a name="operator_neq"></a>  operator! = — Operator

Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora nie jest równa `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Współbieżne wektory nie są równe; `false` współbieżnych wektory są równe.

### <a name="remarks"></a>Uwagi

Dwa wektory współbieżne są takie same, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

##  <a name="operator_lt"></a>  operator&lt; — Operator

Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli współbieżnego wektora po lewej stronie operatora jest mniejszy niż współbieżnego wektora po prawej stronie operatora; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest taka sama jak równorzędny operator dla `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

##  <a name="operator_lt_eq"></a>  operator&lt;= — Operator

Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy niż lub równe `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli współbieżnego wektora po lewej stronie operatora jest mniejszy niż lub równe współbieżnego wektora po prawej stronie operatora; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest taka sama jak równorzędny operator dla `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

##  <a name="operator_gt"></a>  operator&gt; — Operator

Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli współbieżnego wektora po lewej stronie operatora jest większy niż współbieżnego wektora po prawej stronie operatora; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest taka sama jak równorzędny operator dla `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

##  <a name="operator_gt_eq"></a>  operator&gt;= — Operator

Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest większy niż lub równa `concurrent_vector` obiektu po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.

*A1*<br/>
Typ programu przydzielania pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli współbieżnego wektora po lewej stronie operatora jest większy niż lub równy współbieżnego wektora po prawej stronie operatora; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest taka sama jak równorzędny operator dla `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które można modyfikować albo wektorów współbieżnych `_A` lub `_B`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
