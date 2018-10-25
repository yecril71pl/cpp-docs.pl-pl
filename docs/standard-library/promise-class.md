---
title: Promise, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 2b62f4b4be278fc3cc29e32c323c9a0936598d44
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058041"
---
# <a name="promise-class"></a>promise — Klasa

W tym artykule opisano *dostawcę asynchronicznego*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Promise](#promise)|Konstruuje `promise` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get_future](#get_future)|Zwraca [przyszłych](../standard-library/future-class.md) związane z tą obietnicą.|
|[set_exception](#set_exception)|Niepodzielnie Ustawia wynik tej obietnicy, aby wskazać wyjątek.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Niepodzielnie Ustawia wynik tej obietnicy, aby wskazać wyjątek i dostarczyć zawiadomienie zniszczenia tylko obiekty po wszystkich wątków lokalnych w bieżącym wątku (zazwyczaj przy wyjściu wątku).|
|[set_value](#set_value)|Niepodzielnie Ustawia wynik tej obietnicy, aby wskazać wartość.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Niepodzielnie Ustawia wynik tej obietnicy, aby wskazać wartość i zapewnia powiadomienie, które zostały zniszczone tylko obiekty po wszystkich wątków lokalnych w bieżącym wątku (zazwyczaj przy wyjściu wątku).|
|[swap](#swap)|Wymiana *asynchroniczny stan stowarzyszony* tego obiektu obietnicy obiekt promise określony.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Promise::operator =](#op_eq)|Przypisanie udostępnionego stanu obiektu obietnicy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

*Promise*<br/>

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłych >

**Namespace:** standardowe

## <a name="get_future"></a>  Promise::get_future —

Zwraca [przyszłych](../standard-library/future-class.md) obiektu, który ma taką samą *asynchroniczny stan stowarzyszony* jako tej firmy obietnicy.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekt obiecany jest pusty, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający [error_code](../standard-library/error-code-class.md) z `no_state`.

Jeśli ta metoda została już wywołana dla obiektu obiecanego, który ma ten sam asynchronicznego stanu stowarzyszonego, metoda zgłasza `future_error` zawierający `error_code` z `future_already_retrieved`.

## <a name="op_eq"></a>  Promise::operator =

Transfery *asynchroniczny stan stowarzyszony* z określonym `promise` obiektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Element `promise` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Ten operator przesyła asynchronicznego stanu stowarzyszonego z *innych*. Po przesłaniu *innych* jest *pusty*.

## <a name="promise"></a>  Promise::Promise — Konstruktor

Konstruuje `promise` obiektu.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Alokator pamięci. Zobacz [ \<buforów >](../standard-library/allocators-header.md) Aby uzyskać więcej informacji.

*Inne*<br/>
Element `promise` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje *pusty* `promise` obiektu.

Drugi Konstruktor konstruuje pustą `promise` obiektu i zastosowań *Al* dla alokacji pamięci.

Trzeci Konstruktor konstruuje `promise` obiekt i dokonuje transferu asynchronicznego stanu stowarzyszonego z *innych*i pozostawia *innych* puste.

## <a name="set_exception"></a>  Promise::set_exception —

Niepodzielne przechowuje wyjątek w wyniku tego `promise` i ustawia *asynchroniczny stan stowarzyszony* do *gotowe*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Wyłączne*<br/>
[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) przechowywane przez tę metodę jako wynik wyjątku.

### <a name="remarks"></a>Uwagi

Jeśli `promise` obiekt nie ma żadnych asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiekt ma taki sam asynchroniczny stan stowarzyszony, ta metoda wyrzuca `future_error` zawierający kod błędu `promise_already_satisfied`.

W wyniku tej metody wszelkie wątki, które są zablokowane w stowarzyszonym stanie asynchronicznym zostają odblokowane.

## <a name="set_exception_at_thread_exit"></a>  Promise::set_exception_at_thread_exit —

Niepodzielnie Ustawia wynik tej `promise` aby wskazać wyjątek, dostarczając zawiadomienie tylko po wszystkich obiektów lokalnych wątków w bieżącym wątku została zniszczona (zazwyczaj przy wyjściu wątku).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Wyłączne*<br/>
[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) przechowywane przez tę metodę jako wynik wyjątku.

### <a name="remarks"></a>Uwagi

Jeśli obiekt obiecany nie posiada *asynchroniczny stan stowarzyszony*, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value), lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiektu, który ma taką samą asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca `future_error` zawierający kod błędu `promise_already_satisfied`.

W przeciwieństwie do [set_exception](#set_exception), ta metoda nie ustawia asynchronicznego stanu stowarzyszonego na "gotowy" do momentu zniszczenia wszystkich wątków lokalnych obiektów w bieżącym wątku. Zazwyczaj wątki, które są blokowane w stanie stowarzyszonym asynchroniczne nie są odblokowane, dopóki istnieje bieżący wątek.

## <a name="set_value"></a>  Promise::set_value —

Niepodzielne przechowuje wartość jako wynik tej `promise` i ustawia *asynchroniczny stan stowarzyszony* do *gotowe*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, które mają być przechowywane jako wynik.

### <a name="remarks"></a>Uwagi

Jeśli `promise` obiekt nie ma żadnych asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`, lub [set_value_at_thread_exit](#set_value_at_thread_exit) została już wywołana dla `promise` obiektu który ma ten sam asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca `future_error` zawierający kod błędu `promise_already_satisfied`.

W wyniku tej metody wszelkie wątki, które są zablokowane w stowarzyszonym stanie asynchronicznym zostają odblokowane.

Pierwsza metoda generuje również każdy wyjątek, który jest generowany, gdy *Val* jest kopiowana do stanu stowarzyszonego asynchronicznie. W takiej sytuacji, stowarzyszony stan asynchroniczny nie jest ustawiona na gotowe.

Druga metoda generuje również każdy wyjątek, który jest generowany, gdy *Val* jest przenoszony do stanu stowarzyszonego asynchronicznie. W takiej sytuacji, stowarzyszony stan asynchroniczny nie jest ustawiona na gotowe.

Przypadku częściowej specjalizacji `promise<Ty&>`, wartość przechowywana w praktyce jest odwołanie do *Val*.

Dla specjalizacji `promise<void>`, przechowywana wartość nie istnieje.

## <a name="set_value_at_thread_exit"></a>  Promise::set_value_at_thread_exit —

Niepodzielne przechowuje wartość w wyniku tego `promise` obiektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, które mają być przechowywane jako wynik.

### <a name="remarks"></a>Uwagi

Jeśli obiekt obiecany nie posiada *asynchroniczny stan stowarzyszony*, ta metoda wyrzuca [future_error](../standard-library/future-error-class.md) zawierający kod błędu `no_state`.

Jeśli [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), lub `set_value_at_thread_exit` została już wywołana dla `promise` obiektu, który ma taką samą asynchronicznego stanu stowarzyszonego, ta metoda wyrzuca `future_error` zawierający kod błędu `promise_already_satisfied`.

W przeciwieństwie do `set_value`, stowarzyszony stan asynchroniczny nie ustawiono na "gotowy" do momentu zniszczenia wszystkich wątków lokalnych obiektów w bieżącym wątku. Zazwyczaj wątki, które są blokowane w stanie stowarzyszonym asynchroniczne nie są odblokowane, dopóki istnieje bieżący wątek.

Pierwsza metoda generuje również każdy wyjątek, który jest generowany, gdy *Val* jest kopiowana do stanu stowarzyszonego asynchronicznie.

Druga metoda generuje również każdy wyjątek, który jest generowany, gdy *Val* jest przenoszony do stanu stowarzyszonego asynchronicznie.

Przypadku częściowej specjalizacji `promise<Ty&>`, wartość przechowywana jest skutecznym odniesieniem do *Val*.

Dla specjalizacji `promise<void>`, przechowywana wartość nie istnieje.

## <a name="swap"></a>  Promise::swap —

Wymiana *asynchroniczny stan stowarzyszony* z tego obiektu obietnicy określonego obiektu.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Element `promise` obiektu.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
