---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: ed98966f651df76078fa47b05f5a2d8ae1b71d05
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244580"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Określa klasy [condition_variable](../standard-library/condition-variable-class.md) i [condition_variable_any](../standard-library/condition-variable-any-class.md) służące do tworzenia obiektów, które poczekaj, aż zdefiniowany warunek nakazujący są prawdziwe.

Środowisko uruchomieniowe współbieżności (ConcRT) korzysta z tego pliku nagłówkowego, aby można go używać razem z innych mechanizmów ConcRT. Aby uzyskać więcej informacji na temat ConcRT zobacz [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<condition_variable >

**Namespace:** standardowe

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, tego pliku nagłówkowego jest zablokowany.

### <a name="remarks"></a>Uwagi

Kod, który oczekuje zmienną warunek musi także zostać użyta `mutex`. Zablokować wątek wywołujący `mutex` przed wywołaniem funkcji, które oczekiwania dla zmiennej stanu. `mutex` Następnie zostanie zablokowana, gdy wywołana funkcja zwraca. `mutex` Nie jest zablokowany, podczas gdy wątek oczekuje na warunek, którego chcesz stać się wartość true. Tak, aby nie są nieprzewidywalne wyniki, każdy wątek, który oczekuje na zmiennej warunek musi używać tego samego `mutex` obiektu.

Obiekty typu `condition_variable_any` mogą być używane z elementu mutex dowolnego typu. Typ obiektu mutex, która jest używana nie trzeba podawać `try_lock` metody. Obiekty typu `condition_variable` należy używać tylko za pomocą elementu mutex typu `unique_lock<mutex>`. Obiekty tego typu może być szybsza niż obiekty typu `condition_variable_any<unique_lock<mutex>>`.

Oczekiwania na zdarzenie, najpierw zablokować element mutex, a następnie wywołać jedną z `wait` metod na zmiennej stanu. `wait` Wywołania bloki, aż inny wątek sygnalizuje zmiennej stanu.

*Fałszywe wakeups* występują, gdy wątków, które oczekują na zmienne warunków zostają odblokowane bez odpowiednich powiadomień. Rozpoznawanie takie fałszywe wakeups, kod, który oczekuje na warunek, aby stać się true jawnie należy sprawdzić tego warunku, kod zwrócona przez funkcję oczekiwania. Zwykle odbywa się za pomocą pętli. Możesz użyć `wait(unique_lock<mutex>& lock, Predicate pred)` wykonać tę pętlę.

```cpp
while (condition is false)
    wait for condition variable;
```

`condition_variable_any` i `condition_variable` klasy każdy ma trzy metody, które oczekiwania dla warunku.

- `wait` w tym czasie czeka w przedziale czasu niepowiązanych.

- `wait_until` czeka, aż do określonej `time`.

- `wait_for` czeka na określoną `time interval`.

Każda z tych metod ma dwie przeciążone wersje. Tylko jedna czeka i można obudzić błędnie. Druga przyjmuje argument dodatkowe szablony, który definiuje predykat. Metoda nie zwraca do momentu predykat **true**.

Każda klasa ma również dwie metody, które są używane do powiadamiania zmiennej warunku, która jest jego stan **true**.

- `notify_one` zostanie wznowiona jeden z wątków, które oczekuje na zmiennej stanu.

- `notify_all` budzi wszystkie wątki, które oczekują na zmiennej stanu.

## <a name="functions-and-enums"></a>Funkcje i wyliczenia

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable, klasa](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any, klasa](../standard-library/condition-variable-any-class.md)<br/>
