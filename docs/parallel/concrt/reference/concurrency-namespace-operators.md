---
title: Operatory przestrzeni nazw współbieżności
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
ms.openlocfilehash: aac43a15b09bd792118fbfe7ea51493b73b8ac9d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374382"
---
# <a name="concurrency-namespace-operators"></a>Operatory przestrzeni nazw współbieżności

||||
|-|-|-|
|[operator!=](#operator_neq)|[Operator&amp;&amp;](#operator_amp_amp)|[Operator&gt;](#operator_gt)|
|[Operator&gt;=](#operator_gt_eq)|[Operator&lt;](#operator_lt)|[Operator&lt;=](#operator_lt_eq)|
|[operator==](#operator_eq_eq)|[&#124;&#124;operatora](#operator_lor)| |

## <a name="operator124124-operator"></a><a name="operator_lor"></a>operator&#124;&#124; Operator

Tworzy zadanie, które zostanie pomyślnie ukończone, gdy którekolwiek z zadań dostarczonych jako argumenty zakończy się pomyślnie.

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

*Returntype*<br/>
Typ zwróconego zadania.

*Lhs*<br/>
Pierwsze zadanie do połączenia z wynikowego zadania.

*Rhs*<br/>
Drugie zadanie, które ma łączyć w wynikowe zadanie.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które kończy się pomyślnie po pomyślnym zakończeniu jednego z zadań wejściowych. Jeśli zadania wejściowe `T`są typu, dane wyjściowe `task<std::vector<T>`tej funkcji będzie . Jeśli zadania wejściowe `void` są typu, zadaniem `task<void>`wyjściowym będzie również .

### <a name="remarks"></a>Uwagi

Jeśli oba zadania są anulowane lub zgłosić wyjątki, zwrócone zadanie zostanie ukończone w stanie anulowane i jeden z `get()` wyjątków, jeśli wystąpią, zostaną odrzucone podczas wywołania lub `wait()` na to zadanie.

## <a name="operatorampamp-operator"></a><a name="operator_amp_amp"></a>operator&amp; &amp; operatora

Tworzy zadanie, które zostanie pomyślnie ukończone, gdy oba zadania dostarczone jako argumenty zostaną pomyślnie ukończone.

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

*Returntype*<br/>
Typ zwróconego zadania.

*Lhs*<br/>
Pierwsze zadanie do połączenia z wynikowego zadania.

*Rhs*<br/>
Drugie zadanie, które ma łączyć w wynikowe zadanie.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które kończy się pomyślnie po pomyślnym zakończeniu obu zadań wejściowych. Jeśli zadania wejściowe `T`są typu, dane wyjściowe `task<std::vector<T>>`tej funkcji będzie . Jeśli zadania wejściowe `void` są typu, zadaniem `task<void>`wyjściowym będzie również .

### <a name="remarks"></a>Uwagi

Jeśli jedno z zadań zostanie anulowane lub zgłosić wyjątek, zwrócone zadanie zakończy się wcześniej, w stanie anulowane, `get()` `wait()` a wyjątek, jeśli wystąpi, zostanie zgłoszony, jeśli wywołasz lub na to zadanie.

## <a name="operator-operator"></a><a name="operator_eq_eq"></a>operator== Operator

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora `concurrent_vector` jest równy obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator== (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesny wektor po lewej stronie operatora jest równy wektorowi równemu wektorowi równemu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Dwa równoczesnych wektorów są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="operator-operator"></a><a name="operator_neq"></a>operator!= Operator

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora nie `concurrent_vector` jest równy obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesne wektory nie są równe; **false,** jeśli równoczesne wektory są równe.

### <a name="remarks"></a>Uwagi

Dwa równoczesnych wektorów są równe, jeśli mają taką samą liczbę elementów i ich odpowiednie elementy mają te same wartości. W przeciwnym razie są nierówne.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="operatorlt-operator"></a><a name="operator_lt"></a>operator&lt; operatora

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora `concurrent_vector` jest mniejszy niż obiekt po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator<(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesnych wektor po lewej stronie operatora jest mniejsza niż równoczesnych wektor po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z `vector` równoważnym `std` operatorem dla klasy w obszarze nazw.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="operatorlt-operator"></a><a name="operator_lt_eq"></a>operator&lt;= Operator

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora jest mniejszy `concurrent_vector` lub równy obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesny wektor po lewej stronie operatora jest mniejszy lub równy równemu równemu wektorowi równemu po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z `vector` równoważnym `std` operatorem dla klasy w obszarze nazw.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="operatorgt-operator"></a><a name="operator_gt"></a>operator&gt; operatora

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora `concurrent_vector` jest większy niż obiekt po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator>(
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesnych wektor po lewej stronie operatora jest większa niż równoczesnych wektor po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z `vector` równoważnym `std` operatorem dla klasy w obszarze nazw.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="operatorgt-operator"></a><a name="operator_gt_eq"></a>operator&gt;= Operator

Sprawdza, `concurrent_vector` czy obiekt po lewej stronie operatora jest większy `concurrent_vector` lub równy obiektowi po prawej stronie.

```cpp
template<typename T, class A1, class A2>
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,
    const concurrent_vector<T, A2>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*A1*<br/>
Typ alokatora pierwszego `concurrent_vector` obiektu.

*A2*<br/>
Typ alokatora drugiego `concurrent_vector` obiektu.

*_A*<br/>
Obiekt typu `concurrent_vector`.

*_B*<br/>
Obiekt typu `concurrent_vector`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli równoczesny wektor po lewej stronie operatora jest większy lub równy równemu równoczesnego wektora po prawej stronie operatora; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zachowanie tego operatora jest identyczne z `vector` równoważnym `std` operatorem dla klasy w obszarze nazw.

Ta metoda nie jest bezpieczna współbieżności w odniesieniu do innych metod, które `_A` mogą `_B`modyfikować jeden z równoczesnych wektorów lub .

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
