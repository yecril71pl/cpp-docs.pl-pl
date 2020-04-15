---
title: '&lt;przyszłe&gt; funkcje'
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
ms.openlocfilehash: 16c26212cac13602e981f42d8333518da90615fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370663"
---
# <a name="ltfuturegt-functions"></a>&lt;przyszłe&gt; funkcje

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[Wymiany](#swap)|

## <a name="async"></a><a name="async"></a>Async

Reprezentuje *asynchroniiowego dostawcy*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

*Zasad*\
Wartość [uruchomienia.](../standard-library/future-enums.md#launch)

### <a name="remarks"></a>Uwagi

Definicje skrótów:

|||
|-|-|
|*Dfn*|Wynik wywołania `decay_copy(forward<Fn>(fn))`.|
|*dargs (dargs)*|Wyniki rozmów `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty (ty)*|Typ `result_of<Fn(ArgTypes...)>::type`.|

Zwraca pierwszą `async(launch::any, fn, args...)`funkcję szablonu .

Druga funkcja zwraca `future<Ty>` obiekt, którego *skojarzony stan asynchroniczne* przechowuje wynik wraz z wartościami *dfn* i *dargs* oraz obiekt wątku do zarządzania oddzielnym wątkiem wykonania.

O `decay<Fn>::type` ile nie jest to typ inny niż uruchomienie, druga funkcja nie uczestniczy w rozpoznawaniu przeciążenia.

Standard C++ stwierdza, że jeśli zasada jest uruchomiona::async, funkcja tworzy nowy wątek. Jednak implementacja firmy Microsoft jest obecnie niezgodna. Uzyskuje swoje wątki z usługi Windows ThreadPool, która w niektórych przypadkach może zapewnić wątek z recyklingu, a nie nowy. Oznacza to, `launch::async` że polityka jest `launch::async|launch::deferred`rzeczywiście wdrażana jako .  Innym implikacją implementacji opartej na wątkupool jest, że nie ma żadnej gwarancji, że zmienne lokalne wątku zostaną zniszczone po zakończeniu wątku. Jeśli wątek zostanie poddany recyklingowi `async`i dostarczony do nowego wywołania, stare zmienne nadal będą istnieć. Dlatego zaleca się, aby nie używać zmiennych `async`lokalnych wątków z .

Jeśli *policy* zasada `launch::deferred`jest , funkcja oznacza jego skojarzony stan asynchroniczne jako gospodarstwa *odroczonej funkcji* i zwraca. Pierwsze wywołanie dowolnej funkcji nieczasowej, która czeka na skojarzony stan asynchroniczne, aby być `INVOKE(dfn, dargs..., Ty)`gotowym w efekcie wywołuje funkcję odroczoną przez ocenę .

We wszystkich przypadkach skojarzony stan asynchroniczne `future` obiektu nie jest ustawiona na *gotowy,* dopóki ocena `INVOKE(dfn, dargs..., Ty)` zakończy, albo przez zgłaszanie wyjątku lub przez powrót normalnie. Wynik skojarzonego stanu asynchronicznej jest wyjątkiem, jeśli został zgłoszony lub dowolną wartość, która jest zwracana przez ocenę.

> [!NOTE]
> W `future`przypadku (lub ostatniego [shared_future](../standard-library/shared-future-class.md)— dołączonego do zadania `std::async`rozpoczętego z blokiem destruktora, jeśli zadanie nie zostało ukończone; oznacza to, że blokuje, jeśli `.get()` ten `.wait()` wątek nie został jeszcze wywołany lub i zadanie jest nadal uruchomione. Jeśli `future` uzyskane `std::async` z jest przenoszony poza zakres lokalny, inny kod, który używa go należy pamiętać, że jego destruktor może zablokować dla stanu udostępnionego, aby stać się gotowy.

Pseudo-funkcja `INVOKE` jest zdefiniowana w [ \<>funkcjonalnym ](../standard-library/functional.md).

## <a name="future_category"></a><a name="future_category"></a>future_category

Zwraca odwołanie do [obiektu error_category,](../standard-library/error-category-class.md) który charakteryzuje błędy skojarzone `future` z obiektami.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

Tworzy [error_code](../standard-library/error-code-class.md) wraz z [error_category](../standard-library/error-category-class.md) obiektem, który charakteryzuje [przyszłe](../standard-library/future-class.md) błędy.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Wartość [future_errc](../standard-library/future-enums.md#future_errc) identyfikującą zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

Tworzy [error_condition](../standard-library/error-condition-class.md) wraz z [error_category](../standard-library/error-category-class.md) obiektem, który charakteryzuje [przyszłe](../standard-library/future-class.md) błędy.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*Errno*\
Wartość [future_errc](../standard-library/future-enums.md#future_errc) identyfikującą zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a><a name="swap"></a>Wymiany

Wymienia *skojarzony stan asynchroniczne* jednego `promise` obiektu z stanem innego.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Lewej*\
Lewy `promise` obiekt.

*Prawo*\
Właściwy `promise` obiekt.

## <a name="see-also"></a>Zobacz też

[\<przyszłych>](../standard-library/future.md)
