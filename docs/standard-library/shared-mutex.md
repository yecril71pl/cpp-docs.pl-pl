---
title: '&lt;shared_mutex&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
dev_langs:
- C++
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4a9cd6c4533b3b59fdb3c5cab17ffaba071fb08
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

&lt;Shared_mutex > Nagłówek zawiera elementy podstawowe synchronizacji do ochrony danych udostępnionych, którego mogą uzyskać dostęp przez wiele wątków. Oprócz formantu wyłącznego dostępu podany przez klasy obiektu mutex klas udostępnionego obiektu mutex Zezwalaj własność udostępnionego przez wiele wątków z systemem innym niż wyłącznego dostępu. Udostępniony muteksy może służyć do kontrolowania zasobów, które mogą być odczytywane przez kilka wątków bez powodowania wyścigu, ale muszą być zapisane wyłącznie przez pojedynczy wątek.

Nagłówek &lt;shared_mutex > określa klasy `shared_mutex` i `shared_timed_mutex`, klasy szablonu `shared_lock`, a funkcja szablonu `swap` dla obiektu mutex Obsługa udostępnionego.

|Klasy|Opis|
|-------------|-----------------|
|[shared_mutex — klasa](../standard-library/shared-mutex.md#class_shared_mutex)|Typ obiektu mutex udostępnionego, który może być zablokowana przez jednego agenta lub udostępnione-wyłącznie przez kilka agentów.|
|[shared_timed_mutex — klasa](../standard-library/shared-mutex.md#class_shared_timed_mutex)|Typ udostępnionego obiektu mutex czasu, która może być zablokowana przez jednego agenta lub udostępnione-wyłącznie przez kilka agentów.|
|[shared_lock — klasa](../standard-library/shared-mutex.md#class_shared_lock)|Klasa szablonu, która opakowuje udostępnionego obiektu mutex do obsługi operacji czasu blokady i udostępnianie otwarty przez kilka agentów.|

|Funkcje|Opis|
|---------------|-----------------|
|[swap](../standard-library/shared-mutex.md#function_swap)|Zamienia zawartości obiektów udostępnionego obiektu mutex odwołuje się do parametrów funkcji.|

## <a name="syntax"></a>Składnia

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Uwagi

Wystąpienie klasy `shared_mutex` jest *udostępnionego typu obiektu mutex*, typu, który kontroluje udostępnionego własności obiektu mutex w zakresie. Typ obiektu mutex udostępnionego spełnia wszystkie wymagania typu obiektu mutex, a także elementów członkowskich do obsługi udostępnionych własność otwarty.

Typ obiektu mutex udostępnionego obsługuje dodatkowe metody `lock_shared`, `unlock_shared`, i `try_lock_shared`:

- `lock_shared` Metody blokuje wątek wywołujący, dopóki wątek uzyskuje prawo własności do udostępnionego obiektu mutex.

- `unlock_shared` Metoda zwalnia udostępnionego własności obiektu mutex przez wątek wywołujący.

- `try_lock_shared` — Metoda próbuje uzyskać udostępnionego prawo własności obiektu mutex bez blokowania. Jego typem zwracanym jest możliwe do przekonwertowania na `bool` i `true` Jeśli metoda uzyskuje prawo własności, a w przeciwnym razie `false`.

Klasa `shared_timed_mutex` jest *udostępnionego typu czasu obiektu mutex*typu, który spełnia wymagania zarówno udostępnionego obiektu mutex wpisz i wpisz czasu obiektu mutex.

Typ udostępnionego obiektu mutex czasu obsługuje dodatkowe metody `try_lock_shared_for` i `try_lock_shared_until`:

- `try_lock_shared_for` — Metoda próbuje uzyskać prawo własności do udostępnionego obiektu mutex, dopóki nie minął czas trwania, określony przez parametr. Jeśli czas trwania nie jest dodatnia, metoda jest odpowiednikiem `try_lock_shared`. Metoda nie zwraca w czasie trwania określić, jeśli nie są uzyskiwane własność udostępnionego. Jego wartość zwracana jest `true` Jeśli metoda uzyskuje prawo własności, a w przeciwnym razie `false`.

- `try_lock_shared_until` Metoda próbuje uzyskać udostępnionego prawo własności obiektu mutex, dopóki upływie określonego czasu bezwzględnego. Jeśli określona godzina już minęła, metoda jest odpowiednikiem `try_lock_shared`. Metoda nie zwraca przed są uzyskiwane przez czas określony, chyba że udostępniony własności. Jego wartość zwracana jest `true` Jeśli metoda uzyskuje prawo własności, a w przeciwnym razie `false`.

`shared_lock` Klasy szablonu oferuje rozszerzone wsparcie dla upłynął blokowanie i przeniesienie własności udostępnionego obiektu mutex. Prawo własności obiektu mutex można uzyskać na lub po konstrukcji i mogą być przenoszone do innego `shared_lock` obiektu. Obiekty typu `shared_lock` można przenieść, ale nie skopiowany.

> [!WARNING]
> Począwszy od programu Visual Studio 2015, typy synchronizacji standardowa biblioteka C++ są oparte na elementy podstawowe synchronizacji systemu Windows i nie są już używane ConcRT (z wyjątkiem sytuacji, gdy platforma docelowa jest Windows XP). Typy zdefiniowane w &lt;shared_mutex > nie powinien być używany z dowolnym ConcRT typów lub funkcji.

## <a name="classes"></a>Klasy

###  <a name="class_shared_mutex"></a> shared_mutex — klasa

Klasa `shared_mutex` implementuje obiektu mutex niecykliczne z semantyki wspólnej własności.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex — klasa

Klasa `shared_timed_mutex` implementuje obiektu mutex niecykliczne z semantyki własność udostępnionego, który spełnia wymagania typu czasu obiektu mutex.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="&lt;shared"></a> shared_lock — klasa

Szablon klasy `shared_lock` steruje udostępnionego własności obiektu mutex udostępnionych w ramach zakresu. Parametr szablonu musi być typem udostępnionego obiektu mutex.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Funkcje

###  <a name="function_swap"></a> Swap

Zamienia `shared_lock` obiektów.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Zamienia zawartości dwóch `shared_lock` obiektów. Efektywne taki sam, jak `x.swap(y)`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** &lt;shared_mutex >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
[&lt;obiektu mutex >](../standard-library/mutex.md)
