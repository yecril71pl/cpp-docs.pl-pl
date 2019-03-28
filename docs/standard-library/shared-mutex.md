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
ms.openlocfilehash: 97d77399357030feaa90228a1b0cdeb80d48034c
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565389"
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

&lt;Shared_mutex > nagłówka stanowi podstawowych synchronizacji ochrony danych udostępnionych, który może zostać oceniony przez wiele wątków. Oprócz sterowania wyłącznego dostępu, dostarczane przez klasy obiektu mutex klasy udostępnionego obiektu mutex także umożliwić wspólną własność przez wiele wątków niewyłączne dostępu. Udostępnione muteksy może służyć do kontrolowania zasobów, które mogą być odczytywane przez wiele wątków, bez powodowania wyścigu, ale musi być napisany wyłącznie w jednym wątku.

Nagłówek &lt;shared_mutex > określa klasy `shared_mutex` i `shared_timed_mutex`, klasa szablonu `shared_lock`oraz funkcji szablonu `swap` dla obiektu mutex Obsługa udostępnionego.

|Klasy|Opis|
|-------------|-----------------|
|[shared_mutex Class](#class_shared_mutex)|Typ obiektu mutex udostępnionego, który może być zablokowana przez jeden agent lub udostępnione-wyłącznie przez wielu agentów.|
|[shared_timed_mutex klasy](#class_shared_timed_mutex)|Typ udostępnionego mutex Przekroczono limit czasu, który może być zablokowana przez jeden agent lub udostępnione-wyłącznie przez wielu agentów.|
|[shared_lock klasy](#class_shared_lock)|Klasa szablonu, który otacza udostępnionego obiektu mutex do obsługi operacji przekroczono limit czasu blokady i niewyłączną udostępniania przez wielu agentów.|

|Funkcje|Opis|
|---------------|-----------------|
|[swap](#function_swap)|Zamienia zawartości obiektów udostępnionych mutex odwołuje się do parametrów funkcji.|

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

Wystąpienie klasy `shared_mutex` jest *udostępnionego typu obiektu mutex*, typ, który kontroluje wspólnej własności obiektu mutex w obrębie zakresu. Typ udostępnionego obiektu mutex spełnia wszystkie wymagania typu obiektu mutex, jak również elementy członkowskie do obsługi udostępnionych posiadania otwarty.

Typ udostępnionego obiektu mutex obsługuje dodatkowe metody `lock_shared`, `unlock_shared`, i `try_lock_shared`:

- `lock_shared` Metoda blokuje wątek wywołujący, aż wątek uzyskuje wspólnej własności obiektu mutex.

- `unlock_shared` Metoda zwalnia wspólnej własności obiektu mutex posiadaniu wątku wywołującego.

- `try_lock_shared` Metoda próbuje uzyskać wspólnej własności obiektu mutex bez blokowania. Jego typem zwracanym jest konwertowany na **bool** i **true** Jeśli metoda uzyskuje własność, ale w inny sposób **false**.

Klasa `shared_timed_mutex` jest *udostępnionego typu obiektu mutex czasu*, wpisz udostępnionego obiektu mutex typ, który spełnia wymagania obu, i wpisz Przekroczono limit czasu elementu mutex.

Typ udostępnionego mutex czasu obsługuje dodatkowe metody `try_lock_shared_for` i `try_lock_shared_until`:

- `try_lock_shared_for` Metoda próbuje uzyskać wspólnej własności obiektu mutex, dopóki nie czas określony przez parametr został przekazany. Jeśli czas trwania nie jest dodatnią, metoda jest odpowiednikiem `try_lock_shared`. Metoda nie zwraca w trakcie trwania określona, chyba że jest uzyskiwany wspólną własność. Jego wartość zwracana jest **true** Jeśli metoda uzyskuje własność, ale w inny sposób **false**.

- `try_lock_shared_until` Metoda próbuje uzyskać wspólnej własności obiektu mutex do momentu określonego bezwzględnego czasu został przekazany. Jeśli określona godzina już minęła, metoda jest odpowiednikiem `try_lock_shared`. Metoda nie zwraca przed uzyskuje się przez czas określony, chyba że współużytkować własność. Jego wartość zwracana jest **true** Jeśli metoda uzyskuje własność, ale w inny sposób **false**.

`shared_lock` Klasy szablonu rozszerzone wsparcie dla upłynął limit czasu blokowania i przeniesienie prawa własności do udostępnionego obiektu mutex. Własność obiektu mutex można uzyskać na lub po konstrukcji i mogą być przenoszone do innego `shared_lock` obiektu. Obiekty typu `shared_lock` można przenosić, ale nie kopiować.

> [!WARNING]
> Począwszy od programu Visual Studio 2015 standardowej biblioteki języka C++ typów synchronizacji opierają się na podstawowych synchronizacji Windows i nie są już używane ConcRT (z wyjątkiem sytuacji, gdy platformą docelową jest Windows XP). Typy zdefiniowane w &lt;shared_mutex > nie należy używać z dowolnym ConcRT typów lub funkcji.

## <a name="classes"></a>Klasy

###  <a name="class_shared_mutex"></a> shared_mutex klasy

Klasa `shared_mutex` implementuje mutex niecyklicznego z semantyką wspólną własność.

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

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex klasy

Klasa `shared_timed_mutex` implementuje mutex niecyklicznego z semantyką wspólną własność, który spełnia wymagania typu obiektu mutex Przekroczono limit czasu.

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

###  <a name="class_shared_lock"></a> shared_lock klasy

Klasa szablonu `shared_lock` kontroluje wspólnej własności obiektu mutex udostępnionych w obrębie zakresu. Parametr szablonu musi być typem udostępnionego elementu mutex.

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

###  <a name="function_swap"></a> swap

Zamienia `shared_lock` obiektów.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Zamienia zawartości dwóch `shared_lock` obiektów. Skutecznie taka sama, jak `x.swap(y)`.

## <a name="requirements"></a>Wymagania

**Header:** &lt;shared_mutex>

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[&lt;mutex>](../standard-library/mutex.md)
