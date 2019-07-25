---
title: '&lt;funkcje&gt; w przyszłości'
ms.date: 11/04/2016
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: 5435c3b9e10f151fc77c72b58c93510b6a867ce1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447329"
---
# <a name="ltfuturegt-functions"></a>&lt;funkcje&gt; w przyszłości

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>asynchroniczne

Reprezentuje *dostawcę asynchronicznego*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

*zasad*\
Wartość [uruchomienia](../standard-library/future-enums.md#launch) .

### <a name="remarks"></a>Uwagi

Definicje skrótów:

|||
|-|-|
|*dfn*|Wynik wywołania `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Wyniki wywołań `decay_copy(forward<ArgsTypes>(args...))`.|
|*Br*|Typ `result_of<Fn(ArgTypes...)>::type`.|

Funkcja pierwszego szablonu zwraca wartość `async(launch::any, fn, args...)`.

Druga funkcja zwraca obiekt, `future<Ty>` którego *skojarzony stan asynchroniczny* przechowuje wynik wraz z wartościami *DFN* i *dargs* oraz obiektem wątku do zarządzania osobnym wątkiem wykonywania.

Chyba `decay<Fn>::type` że jest typem innym niż uruchamianie, druga funkcja nie uczestniczy w rozpoznawaniu przeciążenia.

Standardowe C++ Stany, które w przypadku uruchamiania zasad:: async, funkcja tworzy nowy wątek. Jednakże implementacja firmy Microsoft jest obecnie niezgodna. Uzyskuje ona wątki z puli wątków systemu Windows, co w niektórych przypadkach może dostarczyć wątek odtwarzany zamiast nowego. Oznacza to, że `launch::async` zasady są faktycznie implementowane `launch::async|launch::deferred`jako.  Inną implikacją implementacji opartą na puli wątków jest to, że nie ma gwarancji, że zmienne lokalne wątku zostaną zniszczone po zakończeniu wątku. Jeśli wątek zostanie odtworzony i udostępniony do nowego wywołania `async`, stare zmienne nadal będą istnieć. Dlatego zalecamy, aby nie używać zmiennych lokalnych wątków w programie `async`.

Jeśli *zasady* są `launch::deferred`, funkcja oznacza swój skojarzony stan asynchroniczny jako zawierający *odroczoną funkcję* i zwraca wartość. Pierwsze wywołanie funkcji niebędącej czasem, która czeka na gotowość skojarzonego stanu asynchronicznego, jest gotowe do wywołania funkcji odroczonej przez ocenę `INVOKE(dfn, dargs..., Ty)`.

We wszystkich przypadkach, skojarzony stan `future` asynchroniczny obiektu nie jest ustawiony na *gotowe* `INVOKE(dfn, dargs..., Ty)` do momentu zakończenia oceny, przez wyrzucanie wyjątku lub przez zwrócenie normalne. Wynikiem skojarzonego stanu asynchronicznego jest wyjątek, jeśli został zgłoszony lub wartość zwracana przez ocenę.

> [!NOTE]
> Dla elementu `future`— lub ostatniej [shared_future](../standard-library/shared-future-class.md)— który jest dołączony do zadania uruchomionego z `std::async`, destruktor blokuje się, jeśli zadanie nie zostało ukończone; oznacza to, że jest blokowane, jeśli `.wait()` ten wątek nie został jeszcze wywołany `.get()` , a zadanie jest nadal działa. Jeśli uzyskana z `std::async` programu jest przenoszona poza zakres lokalny, inny kod, który używa tego, musi mieć świadomość, że jego destruktor może zablokować, aby współużytkowany stan stał się gotowy. `future`

Pseudo funkcja `INVOKE` jest definiowana w [ \<> funkcjonalnej](../standard-library/functional.md).

## <a name="future_category"></a>future_category

Zwraca odwołanie do obiektu [error_category](../standard-library/error-category-class.md) , który charakteryzuje błędy, które są skojarzone z `future` obiektami.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>make_error_code

Tworzy [error_code](../standard-library/error-code-class.md) wraz z obiektem [error_category](../standard-library/error-category-class.md) , który charakteryzuje [przyszłe](../standard-library/future-class.md) błędy.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Wartość [future_errc](../standard-library/future-enums.md#future_errc) , która identyfikuje zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>make_error_condition

Tworzy [error_condition](../standard-library/error-condition-class.md) wraz z obiektem [error_category](../standard-library/error-category-class.md) , który charakteryzuje [przyszłe](../standard-library/future-class.md) błędy.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Wartość [future_errc](../standard-library/future-enums.md#future_errc) , która identyfikuje zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>wymiany

Wymienia *skojarzony stan asynchroniczny* jednego `promise` obiektu z innym.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Lewym*\
Lewy `promise` obiekt.

*Kliknij*\
Prawidłowy `promise` obiekt.

## <a name="see-also"></a>Zobacz także

[\<future>](../standard-library/future.md)
