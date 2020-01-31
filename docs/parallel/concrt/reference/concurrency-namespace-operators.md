---
title: Operatory przestrzeni nazw współbieżności
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 00accee4f28167b94b9193aec6d90f32ed242dbe
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821131"
---
# <a name="concurrency-namespace-operators"></a>Operatory przestrzeni nazw współbieżności

||||
|-|-|-|
|[operator!=](#operator_neq)|[&amp;operatora &amp;](#operator_amp_amp)|[&gt; operatora](#operator_gt)|
|[&gt;operatora =](#operator_gt_eq)|[&lt; operatora](#operator_lt)|[&lt;operatora =](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[operator&#124;&#124;](#operator_lor)| |

##  <a name="operator_lor"></a>operator&#124; &#124; operator

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczonych jako argumenty zakończy się pomyślnie.

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

*Atrybuty*<br/>
Typ zwracanego zadania.

*LHS*<br/>
Pierwsze zadanie do połączenia z wynikiem zadania.

*RHS*<br/>
Drugie zadanie, które ma zostać połączone z wynikiem zadania.

### <a name="return-value"></a>Wartość zwrócona

Zadanie, które zakończyło się pomyślnie, gdy jedno z zadań wejściowych zakończyło się pomyślnie. Jeśli zadania wejściowe są typu `T`, dane wyjściowe tej funkcji będą `task<std::vector<T>`. Jeśli zadania wejściowe są typu `void` zadanie wyjściowe będzie również `task<void>`.

### <a name="remarks"></a>Uwagi

Jeśli oba zadania są anulowane lub zgłaszają wyjątki, zwrócone zadanie zostanie ukończone w stanie anulowane, a jedno z wyjątków, jeśli wystąpi, zostanie zgłoszone podczas wywołania `get()` lub `wait()` w tym zadaniu.

##  <a name="operator_amp_amp"></a>operator&amp;operatora &amp;

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

*Atrybuty*<br/>
Typ zwracanego zadania.

*LHS*<br/>
Pierwsze zadanie do połączenia z wynikiem zadania.

*RHS*<br/>
Drugie zadanie, które ma zostać połączone z wynikiem zadania.

### <a name="return-value"></a>Wartość zwrócona

Zadanie, które zakończy się pomyślnie, gdy oba zadania wejściowe zostały wykonane pomyślnie. Jeśli zadania wejściowe są typu `T`, dane wyjściowe tej funkcji będą `task<std::vector<T>>`. Jeśli zadania wejściowe są typu `void` zadanie wyjściowe będzie również `task<void>`.

### <a name="remarks"></a>Uwagi

Jeśli jedno z zadań zostanie anulowane lub zgłasza wyjątek, zwrócone zadanie zostanie wykonane wcześnie, w stanie anulowanym, a wyjątek, jeśli wystąpi, zostanie zgłoszony w przypadku wywołania `get()` lub `wait()` w tym zadaniu.

##  <a name="operator_eq_eq"></a>operator = = — operator

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest równy obiektowi `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżny wektor po lewej stronie operatora jest równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Dwa współbieżne wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

##  <a name="operator_neq"></a>operator! = — operator

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora nie jest równy obiektowi `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżne wektory nie są równe; **Fałsz** , jeśli współbieżne wektory są równe.

### <a name="remarks"></a>Uwagi

Dwa współbieżne wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

##  <a name="operator_lt"></a>operator&lt; operatora

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest mniejszy niż obiekt `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżny wektor po lewej stronie operatora jest mniejszy od współbieżnego wektora po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z operatorem równoważnym dla klasy `vector` w przestrzeni nazw `std`.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

##  <a name="operator_lt_eq"></a>operator&lt;= — operator

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest mniejszy niż lub równy obiektowi `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżny wektor po lewej stronie operatora jest mniejszy niż lub równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z operatorem równoważnym dla klasy `vector` w przestrzeni nazw `std`.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

##  <a name="operator_gt"></a>operator&gt; operatora

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest większy niż obiekt `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżny wektor po lewej stronie operatora jest większy niż współbieżny wektor po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z operatorem równoważnym dla klasy `vector` w przestrzeni nazw `std`.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

##  <a name="operator_gt_eq"></a>operator&gt;= — operator

Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest większy niż lub równy obiektowi `concurrent_vector` po prawej stronie.

```
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego obiektu `concurrent_vector`.

*A2*<br/>
Typ alokatora drugiego obiektu `concurrent_vector`.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli współbieżny wektor po lewej stronie operatora jest większy niż lub równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z operatorem równoważnym dla klasy `vector` w przestrzeni nazw `std`.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B`.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
