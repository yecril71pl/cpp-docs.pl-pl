---
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
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
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: 5dfb0e858bb412daf159ee9efc7dcc13be690886
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336723"
---
# <a name="ltshared_mutex"></a>&lt;> shared_mutex

Nagłówek &lt;shared_mutex> zapewnia podstawowe synchronizacji dla ochrony udostępnionych danych, które mogą być dostępne dla wielu wątków. Oprócz wyłącznej kontroli dostępu zapewnianej przez klasy mutex, udostępnione klasy mutex umożliwiają również współużytkowanie przez wiele wątków dla dostępu niewyłącznego. Udostępnione muteksy mogą służyć do kontrolowania zasobów, które mogą być odczytywane przez kilka wątków bez powodowania sytuacji wyścigu, ale muszą być zapisywane wyłącznie przez pojedynczy wątek.

&lt;Nagłówek `shared_mutex` shared_mutex> definiuje klasy i `shared_timed_mutex`, szablon `shared_lock`klasy i funkcję `swap` szablonu dla udostępnionej obsługi obiektu mutex.

|Klasy|Opis|
|-------------|-----------------|
|[Klasa shared_mutex](#class_shared_mutex)|Współużytkowany typ obiektu mutex, który może być zablokowany wyłącznie przez jednego agenta lub udostępniony nie wyłącznie przez wielu agentów.|
|[Klasa shared_timed_mutex](#class_shared_timed_mutex)|Współużytkowany typ obiektu mutex, który może być zablokowany wyłącznie przez jednego agenta lub udostępniony nie wyłącznie przez wielu agentów.|
|[Klasa shared_lock](#class_shared_lock)|Szablon klasy, który otacza udostępnionego obiektu mutex do obsługi operacji blokady czasowej i niewyłącznego udostępniania przez wielu agentów.|

|Funkcje|Opis|
|---------------|-----------------|
|[Wymiany](#function_swap)|Zamienia zawartość udostępnionych obiektów mutex, do których odwołują się parametry funkcji.|

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

Wystąpienie klasy `shared_mutex` jest *typem obiektu mutex udostępnionym*, typem, który kontroluje współużytkowane własności obiektu mutex w zakresie. Typ udostępnionego obiektu mutex spełnia wszystkie wymagania typu mutex, a także członków do obsługi współużytkowanych własności niewyłącznej.

Współużytkowane gotex `lock_shared`typ `unlock_shared`obsługuje `try_lock_shared`dodatkowe metody , i:

- Metoda `lock_shared` blokuje wątek wywołujący, dopóki wątek nie uzyska współużytkowania obiektu mutex.

- Metoda `unlock_shared` zwalnia współwłasności obiektu mutex posiadanych przez wątek wywołujący.

- Metoda `try_lock_shared` próbuje uzyskać współwłasność obiektu mutex bez blokowania. Jego typ zwracany jest zamienny na **bool** i jest **true,** jeśli metoda uzyskuje własność, ale w przeciwnym razie jest **false**.

Klasa `shared_timed_mutex` jest *współużytkowane czasowe mutex typu*, typ, który spełnia wymagania zarówno typu udostępnionego obiektu mutex i typu czasowego mutex.

Współużytkowane gotex typu `try_lock_shared_for` czasowego obsługuje dodatkowe metody i: `try_lock_shared_until`

- Metoda `try_lock_shared_for` próbuje uzyskać współwłasność obiektu mutex do czasu upływu czasu trwania określonego przez parametr. Jeśli czas trwania nie jest dodatni, `try_lock_shared`metoda jest równoważna . Metoda nie zwraca w określonym czasie, chyba że zostanie uzyskana współwłasność. Jego wartość zwracana jest **true,** jeśli metoda uzyskuje własność, ale w przeciwnym razie jest **false**.

- Metoda `try_lock_shared_until` próbuje uzyskać współwłasność obiektu mutex, dopóki nie upłynie określony czas bezwzględny. Jeśli określony czas już minął, metoda `try_lock_shared`jest równoważna . Metoda nie zwraca przed określonym czasem, chyba że zostanie uzyskana współwłasność. Jego wartość zwracana jest **true,** jeśli metoda uzyskuje własność, ale w przeciwnym razie jest **false**.

Szablon `shared_lock` klasy rozszerza obsługę blokowania czasowego i przenoszenia własności do udostępnionego obiektu mutex. Własność mutexu może być uzyskana w trakcie budowy lub `shared_lock` po jego zakończeniu i może zostać przeniesiona na inny obiekt. Obiekty typu `shared_lock` mogą być przenoszone, ale nie kopiowane.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 typy synchronizacji biblioteki standardowej języka C++ są oparte na elementów pierwotnych synchronizacji systemu Windows i nie są już używane concrt (z wyjątkiem sytuacji, gdy platformą docelową jest System Windows XP). Typy zdefiniowane w &lt;shared_mutex> nie powinny być używane z żadnymi typami lub funkcjami ConcRT.

## <a name="classes"></a>Klasy

### <a name="shared_mutex-class"></a><a name="class_shared_mutex"></a>Klasa shared_mutex

Klasa `shared_mutex` implementuje niecykliczne mutex z semantyki współużytkowania.

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

### <a name="shared_timed_mutex-class"></a><a name="class_shared_timed_mutex"></a>Klasa shared_timed_mutex

Klasa `shared_timed_mutex` implementuje niecykliczne mutex z semantyki współdzielonej własności, która spełnia wymagania typu czasowego mutex.

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

### <a name="shared_lock-class"></a><a name="class_shared_lock"></a>Klasa shared_lock

Szablon `shared_lock` klasy steruje współwłasnością udostępnionego obiektu mutex w zakresie. Parametr szablonu musi być współużytkowanemu typowi obiektu mutex.

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

### <a name="swap"></a><a name="function_swap"></a>Wymiany

Zamienia `shared_lock` obiekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Wymienia zawartość dwóch `shared_lock` obiektów. Skutecznie taki `x.swap(y)`sam jak .

## <a name="requirements"></a>Wymagania

**Nagłówek:** &lt;shared_mutex>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[&lt;>mutex](../standard-library/mutex.md)
