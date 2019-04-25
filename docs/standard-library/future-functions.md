---
title: '&lt;przyszłe&gt; funkcji'
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
ms.openlocfilehash: 56ae0da7e86e092cee46d24d1a2a27d9d54709e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159512"
---
# <a name="ltfuturegt-functions"></a>&lt;przyszłe&gt; funkcji

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>  asynchroniczne

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

*policy*<br/>
A [Uruchom](../standard-library/future-enums.md#launch) wartość.

### <a name="remarks"></a>Uwagi

Definicje skrótów:

|||
|-|-|
|*dfn*|Wynik wywołania metody `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Wyniki wywołania `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Typ `result_of<Fn(ArgTypes...)>::type`.|

Pierwsza funkcja szablonu zwraca `async(launch::any, fn, args...)`.

Druga funkcja zwraca `future<Ty>` którego *asynchroniczny stan stowarzyszony* zawiera wynik wraz z wartościami *dfn* i *dargs* i wątku obiekt do zarządzania oddzielnym wątku wykonywania.

Chyba że `decay<Fn>::type` jest typem innym niż medialnych, druga funkcja nie uczestniczy w przeciążeniu rozdzielczości.

C++ standard stwierdza, że jeśli zasady są launch::async, funkcja tworzy nowy wątek. Jednak implementacja firmy Microsoft jest obecnie niezgodne. Uzyskuje wątków z puli wątków Windows, co w niektórych przypadkach może dostarczyć odtwarzania wątku, a nie na nową. Oznacza to, że `launch::async` zasad jest faktycznie implementowany jako `launch::async|launch::deferred`.  Domniemanie innego wdrożenia na podstawie puli wątków jest, że nie ma żadnej gwarancji, zmiennych thread-local zostaną usunięte po zakończeniu wątku. Jeśli wątek jest odtwarzania i udostępniane nowe wywołanie w celu `async`, stare zmienne będą nadal istnieć. W związku z tym zaleca się używać zmiennych thread-local o `async`.

Jeśli *zasad* jest `launch::deferred`, funkcja oznacza jego asynchronicznie powiązanym stanie jako gospodarstwa *odroczone funkcji* i zwraca. Pierwsze wywołanie dowolnej funkcji nie upłynął limit czasu oczekiwania na asynchronicznego stanu stowarzyszonego obowiązywać gotowe wywołuje funkcję odroczonego poprzez ocenę `INVOKE(dfn, dargs..., Ty)`.

We wszystkich przypadkach asynchronicznego stanu stowarzyszonego z `future` obiektu nie jest ustawiony na *gotowe* aż do obliczania `INVOKE(dfn, dargs..., Ty)` zakończeniu przez wyrzucanie wyjątku lub przez zwrócenie normalnie. Wynik asynchronicznego stanu stowarzyszonego jest wyjątek, jeśli jeden zgłoszono lub każdą wartość, która jest zwracana przez oceny.

> [!NOTE]
> Dla `future`— lub ostatni [shared_future](../standard-library/shared-future-class.md)— dołączona do pracy z usługą zadania `std::async`, bloki destruktor Jeśli zadanie nie zostało ukończone; oznacza to, blokuje Jeśli tego wątku nie jeszcze wywołana `.get()` lub `.wait()` i nadal jest uruchomione zadanie. Jeśli `future` uzyskany z `std::async` zostanie przeniesiony poza zakresem lokalnym innego kodu, który korzysta z niego należy pamiętać, że jego destruktor mogą blokować udostępnionego stanu będzie gotowa.

Pseudo-funkcja `INVOKE` jest zdefiniowany w [ \<funkcjonalności >](../standard-library/functional.md).

## <a name="future_category"></a>  future_category —

Zwraca odwołanie do [error_category](../standard-library/error-category-class.md) obiektu, który charakteryzuje się błędy, które są skojarzone z `future` obiektów.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code —

Tworzy [error_code](../standard-library/error-code-class.md) wraz z [error_category](../standard-library/error-category-class.md) obiektu, który charakteryzuje [przyszłych](../standard-library/future-class.md) błędy.

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*numer błędu*<br/>
A [future_errc](../standard-library/future-enums.md#future_errc) wartość, która identyfikuje zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition —

Tworzy [error_condition](../standard-library/error-condition-class.md) wraz z [error_category](../standard-library/error-category-class.md) obiektu, który charakteryzuje [przyszłych](../standard-library/future-class.md) błędy.

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parametry

*numer błędu*<br/>
A [future_errc](../standard-library/future-enums.md#future_errc) wartość, która identyfikuje zgłoszony błąd.

### <a name="return-value"></a>Wartość zwracana

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  swap

Wymiana *asynchroniczny stan stowarzyszony* jednego `promise` obiektu z innego.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Po lewej stronie `promise` obiektu.

*po prawej stronie*<br/>
Po prawej stronie `promise` obiektu.

## <a name="see-also"></a>Zobacz także

[\<future>](../standard-library/future.md)<br/>
