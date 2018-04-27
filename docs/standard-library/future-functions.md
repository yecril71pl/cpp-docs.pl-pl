---
title: '&lt;przyszłe&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
caps.latest.revision: 11
manager: ghogen
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: e796420f285685c448b3422fe68f0a93daa13fdf
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltfuturegt-functions"></a>&lt;przyszłe&gt; funkcji

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>  Asynchroniczne

Reprezentuje *asynchroniczne dostawcy*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parametry

`policy` A [uruchamianie](../standard-library/future-enums.md#launch) wartość.

### <a name="remarks"></a>Uwagi

Definicje skrótów:

|||
|-|-|
|*dfn*|Wyniku wywołania metody `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Wyniki wywołania `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

Zwraca pierwszy funkcji szablonu `async(launch::any, fn, args...)`.

Zwraca funkcji second `future<Ty>` którego *skojarzony stan asynchronicznego* przechowuje wynik wraz z wartościami *dfn* i *dargs* i wątku obiekt do zarządzania oddzielnym wątku wykonywania.

O ile `decay<Fn>::type` jest typu innego niż uruchamiania, funkcji second nie uczestniczy w Rozpoznanie przeciążenia.

Jeśli `policy` jest `launch::any`, funkcja może wybrać `launch::async` lub `launch::deferred`. W tej implementacji korzysta z funkcji `launch::async`.

Jeśli `policy` jest `launch::async`, funkcja ta umożliwia tworzenie wątku, który daje w wyniku `INVOKE(dfn, dargs..., Ty)`. Funkcja zwraca po utworzeniu wątek bez oczekiwania na wyniki. Jeśli system nie może rozpocząć nowego wątku, funkcja zwraca [system_error —](../standard-library/system-error-class.md) mający z kodem błędu `resource_unavailable_try_again`.

Jeśli `policy` jest `launch::deferred`, funkcja oznacza jego skojarzony stan asynchronicznych jako gospodarstwa *odroczone funkcji* i zwraca. W pierwszym wywołaniu dowolnej — upłynął funkcji czeka na skojarzony stan asynchronicznego obowiązywać do gotowy wywołuje funkcję odroczonego wyniku obliczenia `INVOKE(dfn, dargs..., Ty)`.

We wszystkich przypadkach, skojarzony stan asynchronicznego `future` obiektu nie jest ustawiony na *gotowe* do oceny `INVOKE(dfn, dargs..., Ty)` zakończeniu przez Zgłaszanie wyjątku lub zwracanie normalnie. Wynik skojarzony stan asynchroniczne jest, jeśli jeden został zgłoszony wyjątek lub każdą wartość, która jest zwracana w wyniku obliczania.

> [!NOTE]
> Dla `future`— lub ostatni [shared_future —](../standard-library/shared-future-class.md)— dołączona do pracy z zadaniem `std::async`, bloki destruktora Jeśli zadanie nie zostało ukończone; oznacza to, blokuje Jeśli tego wątku nie jeszcze wywołana `.get()` lub `.wait()` i zadanie jest uruchomione. Jeśli `future` uzyskane z `std::async` przeniesiona poza zakres lokalny innego kodu, który korzysta z niego, należy pamiętać, że jego destruktora może blokować udostępnionego stanu będzie gotowa.

Pseudo-funkcja `INVOKE` jest zdefiniowany w [ \<funkcjonalności >](../standard-library/functional.md).

## <a name="future_category"></a>  future_category —

Zwraca odwołanie do [error_category —](../standard-library/error-category-class.md) obiektu, która charakteryzuje się błędy, które są skojarzone z `future` obiektów.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code —

Tworzy [error_code —](../standard-library/error-code-class.md) razem z [error_category —](../standard-library/error-category-class.md) obiekt, który charakteryzuje [przyszłych](../standard-library/future-class.md) błędy.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

`Errno` A [future_errc —](../standard-library/future-enums.md#future_errc) wartość, która identyfikuje zgłoszonego błędu.

### <a name="return-value"></a>Wartość zwracana

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition —

Tworzy [error_condition —](../standard-library/error-condition-class.md) razem z [error_category —](../standard-library/error-category-class.md) obiekt, który charakteryzuje [przyszłych](../standard-library/future-class.md) błędy.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

`Errno` A [future_errc —](../standard-library/future-enums.md#future_errc) wartość, która identyfikuje zgłoszonego błędu.

### <a name="return-value"></a>Wartość zwracana

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  Swap

Wymiany *skojarzony stan asynchronicznego* jednego `promise` innego obiektu.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

`Left` Po lewej stronie `promise` obiektu.

`Right` Prawo `promise` obiektu.

## <a name="see-also"></a>Zobacz także

[\<future>](../standard-library/future.md)<br/>
