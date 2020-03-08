---
title: '&lt;przyszłych funkcji&gt;'
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865180"
---
# <a name="ltfuturegt-functions"></a>&lt;przyszłych funkcji&gt;

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[wymiany](#swap)|

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

\ *zasad*
Wartość [uruchomienia](../standard-library/future-enums.md#launch) .

### <a name="remarks"></a>Uwagi

Definicje skrótów:

|||
|-|-|
|*dfn*|Wynik wywołania `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Wyniki wywołań `decay_copy(forward<ArgsTypes>(args...))`.|
|*Br*|Typ `result_of<Fn(ArgTypes...)>::type`.|

Pierwsza funkcja szablonu zwraca `async(launch::any, fn, args...)`.

Druga funkcja zwraca obiekt `future<Ty>`, którego *skojarzony stan asynchroniczny* przechowuje wynik wraz z wartościami *DFN* i *dargs* i obiektem wątku do zarządzania osobnym wątkiem wykonywania.

Chyba że `decay<Fn>::type` jest typem innym niż uruchamianie, druga funkcja nie uczestniczy w przeciążeniu.

Standardowe C++ Stany, które w przypadku uruchamiania zasad:: async, funkcja tworzy nowy wątek. Jednakże implementacja firmy Microsoft jest obecnie niezgodna. Uzyskuje ona wątki z puli wątków systemu Windows, co w niektórych przypadkach może dostarczyć wątek odtwarzany zamiast nowego. Oznacza to, że zasady `launch::async` są faktycznie implementowane jako `launch::async|launch::deferred`.  Inną implikacją implementacji opartą na puli wątków jest to, że nie ma gwarancji, że zmienne lokalne wątku zostaną zniszczone po zakończeniu wątku. Jeśli wątek zostanie odtworzony i udostępniony do nowego wywołania `async`, nadal będą istnieć stare zmienne. Dlatego zaleca się, aby nie używać zmiennych lokalnych wątków w `async`.

Jeśli *zasady* są `launch::deferred`, funkcja oznacza swój skojarzony stan asynchroniczny jako zawierający *odroczoną funkcję* i zwraca wartość. Pierwsze wywołanie do dowolnej funkcji niebędącej czasem, która czeka na gotowość skojarzonego stanu asynchronicznego, w efekcie wywołuje odroczoną funkcję przez obliczenie `INVOKE(dfn, dargs..., Ty)`.

We wszystkich przypadkach, skojarzony stan asynchroniczny obiektu `future` nie jest ustawiony na *gotowe* do momentu zakończenia oceny `INVOKE(dfn, dargs..., Ty)`, przez wyrzucanie wyjątku lub przez zwrócenie normalne. Wynikiem skojarzonego stanu asynchronicznego jest wyjątek, jeśli został zgłoszony lub wartość zwracana przez ocenę.

> [!NOTE]
> W przypadku `future`— lub ostatniego [shared_future](../standard-library/shared-future-class.md)— który jest dołączony do zadania uruchomionego z `std::async`, destruktor blokuje się, jeśli zadanie nie zostało ukończone; oznacza to, że blokuje, czy ten wątek nie wywołał jeszcze `.get()` lub `.wait()`, a zadanie jest nadal uruchomione. Jeśli `future` uzyskany z `std::async` jest przenoszony poza zakres lokalny, inny kod, który używa tego, musi mieć świadomość, że jego destruktor może zablokować, aby współużytkowany stan stał się gotowy.

`INVOKE` pseudo funkcja jest definiowana w [\<funkcjonalnej >](../standard-library/functional.md).

## <a name="future_category"></a>future_category

Zwraca odwołanie do obiektu [error_category](../standard-library/error-category-class.md) , który charakteryzuje błędy, które są skojarzone z obiektami `future`.

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

\ *lewo*
Obiekt `promise` po lewej stronie.

*Prawa*\
Właściwy `promise` obiektu.

## <a name="see-also"></a>Zobacz także

[\<przyszłość >](../standard-library/future.md)
