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
ms.openlocfilehash: 7dd72550bc8658158b399e88573526269202f8f4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450435"
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

Nagłówek &lt;> shared_mutex zawiera elementy pierwotne synchronizacji na potrzeby ochrony danych udostępnionych, do których można uzyskać dostęp za pomocą wielu wątków. Oprócz wyłącznej kontroli dostępu dostarczonej przez klasy muteksów współużytkowane klasy muteksów umożliwiają również współużytkowanie własności przez wiele wątków dla niewyłącznego dostępu. Współdzielone muteksy mogą służyć do kontrolowania zasobów, które mogą być odczytywane przez kilka wątków bez powodowania sytuacji wyścigu, ale muszą być zapisywane wyłącznie na podstawie jednego wątku.

Nagłówek &lt;shared_mutex > definiuje klasy `shared_mutex` i `shared_timed_mutex`, klasę `shared_lock`szablonu i funkcję `swap` szablonu do obsługi udostępnionego obiektu mutex.

|Klasy|Opis|
|-------------|-----------------|
|[Klasa shared_mutex](#class_shared_mutex)|Typ udostępnionego obiektu mutex, który może być zablokowany wyłącznie przez jednego agenta lub udostępniony nieprzeznaczony wyłącznie dla wielu agentów.|
|[Klasa shared_timed_mutex](#class_shared_timed_mutex)|Udostępniony typ muteksu czasu, który może być zablokowany wyłącznie przez jednego agenta lub udostępniony nieprzeznaczony wyłącznie dla wielu agentów.|
|[Klasa shared_lock](#class_shared_lock)|Klasa szablonu, która otacza współużytkowany element mutex w celu obsługi operacji blokady czasowej i niewyłącznego udostępniania przez wielu agentów.|

|Funkcje|Opis|
|---------------|-----------------|
|[swap](#function_swap)|Zamienia zawartość udostępnionych obiektów mutex, do których odwołują się parametry funkcji.|

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

Wystąpienie klasy `shared_mutex` jest *wspólnym typem elementu mutex*, typem, który kontroluje współużytkowany własność obiektu mutex w zakresie. Współużytkowany typ muteksu spełnia wszystkie wymagania typu muteksu, a także składowe do obsługi udostępnionej niewyłącznej własności.

Typ udostępnionego obiektu mutex obsługuje dodatkowe metody `lock_shared`, `unlock_shared`i `try_lock_shared`:

- `lock_shared` Metoda blokuje wątek wywołujący do momentu, gdy wątek uzyska wspólną własność obiektu mutex.

- `unlock_shared` Metoda zwalnia wspólną własność obiektu mutex przechowywanego przez wątek wywołujący.

- `try_lock_shared` Metoda próbuje uzyskać współużytkowany własność obiektu mutex bez blokowania. Typ zwracany jest konwertowany na **bool** i ma **wartość true** , jeśli metoda uzyskuje własność, ale w przeciwnym razie ma **wartość false**.

Klasa `shared_timed_mutex` jest udostępnionym *typem obiektu mutex*, który spełnia wymagania zarówno typu elementu udostępnionego obiektu mutex, jak i typu muteksu czasu.

Udostępniony typ muteksu czasu obsługuje dodatkowe metody `try_lock_shared_for` i: `try_lock_shared_until`

- `try_lock_shared_for` Metoda próbuje uzyskać udostępnioną własność obiektu mutex do momentu, gdy czas określony przez parametr zostanie zakończony. Jeśli czas trwania nie jest dodatni, metoda jest równoważna z `try_lock_shared`. Metoda nie zwraca wartości w czasie trwania określonym, o ile nie zostanie uzyskana udostępniona własność. Wartość zwracana jest **true** , jeśli metoda uzyskuje własność, ale w przeciwnym razie **zwraca wartość false**.

- `try_lock_shared_until` Metoda próbuje uzyskać udostępnioną własność obiektu mutex do momentu przekazania określonego czasu bezwzględnego. Jeśli określony czas już przeszedł, metoda jest równoważna z `try_lock_shared`. Metoda nie zwraca przed upływem określonego czasu, o ile nie zostanie uzyskana udostępniona własność. Wartość zwracana jest **true** , jeśli metoda uzyskuje własność, ale w przeciwnym razie **zwraca wartość false**.

Klasa `shared_lock` szablonu rozszerza obsługę blokowania czasowego i przenoszenia własności do udostępnionego obiektu mutex. Własność obiektu mutex może być uzyskana w konstrukcji lub po nim i może zostać przeniesiona do `shared_lock` innego obiektu. Obiekty typu `shared_lock` można przenosić, ale nie są kopiowane.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 typy C++ synchronizacji biblioteki standardowej są oparte na prymitywach synchronizacji systemu Windows i nie używają już ConcRT (z wyjątkiem sytuacji, gdy platforma docelowa to system Windows XP). Typów zdefiniowanych w &lt;shared_mutex > nie należy używać z żadnymi typami ConcRT ani funkcjami.

## <a name="classes"></a>Klasy

###  <a name="class_shared_mutex"></a>Klasa shared_mutex

Klasa `shared_mutex` implementuje niecykliczny element mutex z semantyką własności udostępnionej.

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

###  <a name="class_shared_timed_mutex"></a>Klasa shared_timed_mutex

Klasa `shared_timed_mutex` implementuje niecykliczny element mutex z semantyką własności współużytkowanej, która spełnia wymagania typu obiektu mutex o określonej godzinie.

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

###  <a name="class_shared_lock"></a>Klasa shared_lock

Klasa `shared_lock` szablonu kontroluje wspólną własność udostępnionego obiektu mutex w zakresie. Parametr szablonu musi być typem udostępnionego obiektu mutex.

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

###  <a name="function_swap"></a>wymiany

`shared_lock` Zamienia obiekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Wymienia zawartość dwóch `shared_lock` obiektów. Efektywnie tak samo jak `x.swap(y)`w przypadku programu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** &lt;shared_mutex >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[&lt;mutex>](../standard-library/mutex.md)
