---
title: Operatory przestrzeni nazw współbieżności
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: 6cef9304be17dd39e0f0b020133abd08f07fba7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194384"
---
# <a name="concurrency-namespace-operators"></a>Operatory przestrzeni nazw współbieżności

||||
|-|-|-|
|[operator! =](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|
|[operator = =](#operator_eq_eq)|[&#124;&#124;operatora](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>operator&#124;&#124; operatora

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczonych jako argumenty zakończy się pomyślnie.

```cpp
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

### <a name="return-value"></a>Wartość zwracana

Zadanie, które zakończyło się pomyślnie, gdy jedno z zadań wejściowych zakończyło się pomyślnie. Jeśli zadania wejściowe są typu `T` , danymi wyjściowymi tej funkcji będą `task<std::vector<T>` . Jeśli zadania wejściowe są typu **`void`** , zadanie wyjściowe również będzie `task<void>` .

### <a name="remarks"></a>Uwagi

Jeśli oba zadania są anulowane lub zgłaszają wyjątki, zwrócone zadanie zostanie ukończone w stanie anulowane, a jedno z wyjątków, jeśli wystąpi, zostanie zgłoszone po wywołaniu `get()` lub `wait()` w tym zadaniu.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>&amp; &amp; operator operator

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy oba zadania dostarczone jako argumenty zakończą się pomyślnie.

```cpp
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

### <a name="return-value"></a>Wartość zwracana

Zadanie, które zakończy się pomyślnie, gdy oba zadania wejściowe zostały wykonane pomyślnie. Jeśli zadania wejściowe są typu `T` , danymi wyjściowymi tej funkcji będą `task<std::vector<T>>` . Jeśli zadania wejściowe są typu **`void`** , zadanie wyjściowe również będzie `task<void>` .

### <a name="remarks"></a>Uwagi

Jeśli jedno z zadań zostanie anulowane lub zgłosi wyjątek, zwrócone zadanie zakończy się wcześnie, w stanie anulowanym, a wyjątek, jeśli wystąpi, zostanie wygenerowany w przypadku wywołania `get()` lub `wait()` wykonania tego zadania.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>operator = = — operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest równy `concurrent_vector` obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor współbieżny po lewej stronie operatora jest równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Dwa współbieżne wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="operator-operator"></a><a name="operator_neq"></a>operator! = — operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora nie jest równy `concurrent_vector` obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli współbieżne wektory nie są równe; **`false`** Jeśli współbieżne wektory są równe.

### <a name="remarks"></a>Uwagi

Dwa współbieżne wektory są równe, jeśli mają taką samą liczbę elementów, a ich odpowiednie elementy mają takie same wartości. W przeciwnym razie są one nierówne.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>&lt;operator operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od `concurrent_vector` obiektu po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor współbieżny po lewej stronie operatora jest mniejszy od współbieżnego wektora po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest takie samo jak odpowiednik operatora `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>operator &lt; = — operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od lub równy `concurrent_vector` obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor współbieżny po lewej stronie operatora jest mniejszy niż lub równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest takie samo jak odpowiednik operatora `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>&gt;operator operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż `concurrent_vector` obiekt po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor współbieżny po lewej stronie operatora jest większy niż współbieżny wektor po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest takie samo jak odpowiednik operatora `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>operator &gt; = — operator

Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż lub równy `concurrent_vector` obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ programu przydzielania drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wektor współbieżny po lewej stronie operatora jest większy niż lub równy współbieżnemu wektorowi po prawej stronie operatora; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest takie samo jak odpowiednik operatora `vector` klasy w `std` przestrzeni nazw.

Ta metoda nie jest bezpieczna pod kątem współbieżności w odniesieniu do innych metod, które mogą zmodyfikować jeden z współbieżnych wektorów `_A` lub `_B` .

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
