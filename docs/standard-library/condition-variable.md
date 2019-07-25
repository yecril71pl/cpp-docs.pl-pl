---
title: '&lt;condition_variable&gt;'
ms.date: 11/04/2016
f1_keywords:
- <condition_variable>
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
ms.openlocfilehash: e63dc5a494f471997c28be8b2cd237aba45a6fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457386"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Definiuje klasy [condition_variable](../standard-library/condition-variable-class.md) i [condition_variable_any](../standard-library/condition-variable-any-class.md) , które są używane do tworzenia obiektów, które oczekują na spełnienie warunku.

Ten nagłówek używa środowisko uruchomieniowe współbieżności (ConcRT), aby można było używać go razem z innymi mechanizmami ConcRT. Aby uzyskać więcej informacji na temat ConcRT, zobacz [środowisko uruchomieniowe współbieżności](../parallel/concrt/concurrency-runtime.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<condition_variable >

**Przestrzeń nazw:** std

> [!NOTE]
> W kodzie, który jest kompilowany przy użyciu **/CLR**, ten nagłówek jest zablokowany.

### <a name="remarks"></a>Uwagi

Kod, który czeka dla zmiennej warunku, musi również `mutex`używać elementu. Wątek wywołujący musi blokować `mutex` przed wywołaniem funkcji, które oczekują na zmienną warunku. Po wywołaniu wywoływana funkcja jestblokowana.`mutex` Nie `mutex` jest zablokowany, gdy wątek czeka na warunek, aby stał się spełniony. Aby nie miały żadnych nieprzewidzianych wyników, każdy wątek, który czeka na zmienną warunku, musi używać tego `mutex` samego obiektu.

Obiekty typu `condition_variable_any` mogą być używane z mutex dowolnego typu. Typ obiektu mutex, który jest używany, nie musi podawać `try_lock` metody. Obiektów typu `condition_variable` można używać tylko z obiektem mutex typu `unique_lock<mutex>`. Obiekty tego typu mogą być szybsze niż obiekty typu `condition_variable_any<unique_lock<mutex>>`.

Aby poczekać na zdarzenie, najpierw Zablokuj element mutex, a następnie Wywołaj `wait` jedną z metod dla zmiennej warunku. Bloki `wait` wywołań do momentu, gdy inny wątek sygnalizuje zmienną warunku.

*Wznawianie fałszywe* odbywa się, gdy wątki oczekujące na zmienne warunku staną się odblokowane bez odpowiednich powiadomień. Aby można było rozpoznać takie wznowienie fałszywe, kod, który czeka na warunek do jego działania, powinien jawnie sprawdzić ten warunek, gdy kod wraca z funkcji oczekiwania. Jest to zwykle realizowane przy użyciu pętli; Możesz użyć `wait(unique_lock<mutex>& lock, Predicate pred)` , aby wykonać tę pętlę.

```cpp
while (condition is false)
    wait for condition variable;
```

Klasy `condition_variable_any` i`condition_variable` mają trzy metody, które oczekują na warunek.

- `wait`czeka na nieokreślony czas.

- `wait_until`czeka do określonego `time`.

- `wait_for`czeka na określony `time interval`.

Każda z tych metod ma dwie przeciążone wersje. Zaraz czeka i można wzbudzać obudzić. Druga przyjmuje dodatkowy argument szablonu, który definiuje predykat. Metoda nie zwraca do momentu, gdy predykat ma **wartość true**.

Każda klasa ma także dwie metody, które są używane do powiadamiania zmiennej warunku o stanie **true**.

- `notify_one`wznawia jeden z wątków, które oczekują na zmienną warunku.

- `notify_all`wznawia wszystkie wątki oczekujące na zmienną warunku.

## <a name="functions-and-enums"></a>Funkcje i wyliczenia

```cpp
void notify_all_at_thread_exit(condition_variable& cond, unique_lock<mutex> lk);

enum class cv_status { no_timeout, timeout };
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Klasa condition_variable](../standard-library/condition-variable-class.md)\
[condition_variable_any, klasa](../standard-library/condition-variable-any-class.md)
