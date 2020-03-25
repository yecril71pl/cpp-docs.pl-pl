---
title: Klasa lock
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: c8056146998443f4e24169a4464b834d8eff29b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208530"
---
# <a name="lock-class"></a>Klasa lock

Ta klasa automatyzuje blokadę do synchronizowania dostępu do obiektu z kilku wątków.  Gdy jest konstruowany, uzyskuje blokadę i gdy zniszczy, zwalnia blokadę.

## <a name="syntax"></a>Składnia

```cpp
ref class lock;
```

## <a name="remarks"></a>Uwagi

`lock` jest dostępny tylko dla obiektów CLR i może być używany tylko w kodzie CLR.

Wewnętrznie, Klasa Lock używa <xref:System.Threading.Monitor> do synchronizowania dostępu. Aby uzyskać więcej informacji, zobacz artykuł, którego dotyczy odwołanie.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[lock::lock](#lock)|Konstruuje obiekt `lock`, opcjonalnie oczekując na uzyskanie blokady w nieskończoność, przez określony czas lub wcale.|
|[lock::~lock](#tilde-lock)|Destruktory obiektu `lock`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[lock::acquire](#acquire)|Uzyskuje blokadę obiektu, opcjonalnie oczekując na uzyskanie blokady w nieskończoność, przez określony czas lub wcale.|
|[lock::is_locked](#is-locked)|Wskazuje, czy blokada jest utrzymywana.|
|[lock::release](#release)|Zwalnia blokadę.|
|[lock::try_acquire](#try-acquire)|Uzyskuje blokadę obiektu, czeka na określoną ilość czasu i zwraca `bool`, aby zgłosić powodzenie nabycia zamiast zgłaszania wyjątku.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[Lock:: operator&nbsp;bool](#operator-bool)|Operator służący do używania `lock` w wyrażeniu warunkowym.|
|[lock::operator==](#operator-equality)|Operator równości.|
|[lock::operator!=](#operator-inequality)|Operator nierówności.|

## <a name="requirements"></a>Wymagania

**Plik nagłówka** \<msclr\lock.h >

Msclr **przestrzeni nazw**

## <a name="locklock"></a><a name="lock"></a>Lock:: Lock

Konstruuje obiekt `lock`, opcjonalnie oczekując na uzyskanie blokady w nieskończoność, przez określony czas lub wcale.

```cpp
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

### <a name="parameters"></a>Parametry

*_object*<br/>
Obiekt, który ma być zablokowany.

*_timeout*<br/>
Wartość limitu czasu w milisekundach lub jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Wyjątki

Zgłasza <xref:System.ApplicationException>, jeśli nie nastąpiło przekroczenie limitu czasu blokady.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formy konstruktora próbują uzyskać blokadę na `_object` w określonym przedziale czasu (lub <xref:System.Threading.Timeout.Infinite>, jeśli nie jest określony).

Czwarta postać konstruktora nie uzyskuje blokady na `_object`. `lock_later` jest członkiem [lock_when enum](../dotnet/lock-when-enum.md). Użyj [blokady:: Acquire](../dotnet/lock-acquire.md) lub [lock:: try_acquire](../dotnet/lock-try-acquire.md) w celu uzyskania blokady w tym przypadku.

Blokada zostanie automatycznie wydana po wywołaniu destruktora.

nie można <xref:System.Threading.ReaderWriterLock>`_object`.  Jeśli tak, zostanie zwrócony błąd kompilatora.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach. Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku. Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka, aż wszystkie wątki robocze zakończą zadania.

```cpp
// msl_lock_lock.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="locklock"></a><a name="tilde-lock"></a>Lock:: ~ Lock

Destruktory obiektu `lock`.

```cpp
~lock();
```

### <a name="remarks"></a>Uwagi

Destruktor wywołuje [blokadę:: Release](../dotnet/lock-release.md).

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach.  Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku.  Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka, aż wszystkie wątki robocze zakończą zadania.

```cpp
// msl_lock_dtor.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockacquire"></a><a name="acquire"></a>Blokada:: pozyskiwanie

Uzyskuje blokadę obiektu, opcjonalnie oczekując na uzyskanie blokady w nieskończoność, przez określony czas lub wcale.

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parametry

*_timeout*<br/>
Wartość limitu czasu w milisekundach lub jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Wyjątki

Zgłasza <xref:System.ApplicationException>, jeśli nie nastąpiło przekroczenie limitu czasu blokady.

### <a name="remarks"></a>Uwagi

Jeśli wartość limitu czasu nie zostanie podana, domyślnym limitem czasu jest <xref:System.Threading.Timeout.Infinite>.

Jeśli blokada została już uzyskana, ta funkcja nic nie robi.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach.  Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku. Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka, aż wszystkie wątki robocze zakończą zadania.

```cpp
// msl_lock_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockis_locked"></a><a name="is-locked"></a>Blokada:: is_locked

Wskazuje, czy blokada jest utrzymywana.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Wartość zwracana

`true`, jeśli blokada jest utrzymywana, `false` w przeciwnym razie.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach.  Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku.  Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją i czy czekają na zakończenie, dopóki wszystkie wątki robocze nie ukończyą swoich zadań.

```cpp
// msl_lock_is_locked.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l.is_locked()) { // check if we got the lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>Lock:: operator — bool

Operator służący do używania `lock` w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true`, jeśli blokada jest utrzymywana, `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator jest faktycznie konwertowany na `_detail_class::_safe_bool`, który jest bezpieczniejszy niż `bool`, ponieważ nie można go przekonwertować na typ całkowity.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach.  Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku. Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka na zakończenie, dopóki wszystkie wątki robocze nie ukończyją swoich zadań.

```cpp
// msl_lock_op_bool.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l) { // use bool operator to check for lock
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockrelease"></a><a name="release"></a>Lock:: Release

Zwalnia blokadę.

```cpp
void release();
```

### <a name="remarks"></a>Uwagi

Jeśli blokada nie jest utrzymywana, `release` nic nie robi.

Nie musisz jawnie wywoływać tej funkcji. Gdy obiekt `lock` wykracza poza zakres, jego destruktor wywołuje `release`.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach. Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku. Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka, aż wszystkie wątki robocze zakończą zadania.

```cpp
// msl_lock_release.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="locktry_acquire"></a><a name="try-acquire"></a>Blokada:: try_acquire

Uzyskuje blokadę obiektu, czeka na określoną ilość czasu i zwraca `bool`, aby zgłosić powodzenie nabycia zamiast zgłaszania wyjątku.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parametry

*_timeout*<br/>
Wartość limitu czasu w milisekundach lub jako <xref:System.TimeSpan>.

### <a name="return-value"></a>Wartość zwracana

`true`, jeśli Blokada została uzyskana, `false` w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli blokada została już uzyskana, ta funkcja nic nie robi.

### <a name="example"></a>Przykład

W tym przykładzie jest stosowane pojedyncze wystąpienie klasy w wielu wątkach. Klasa używa blokady w celu upewnienia się, że dostęp do jego danych wewnętrznych jest spójny dla każdego wątku. Wątek aplikacji głównej używa blokady w tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy istnieją wątki robocze nadal istnieją. Główna aplikacja czeka, aż wszystkie wątki robocze zakończą zadania.

```cpp
// msl_lock_try_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator"></a><a name="operator-equality"></a>Lock:: operator = =

Operator równości.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Obiekt, który ma zostać porównany pod kątem równości.

### <a name="return-value"></a>Wartość zwracana

Zwraca `true`, jeśli `t` jest taka sama jak obiekt blokady, `false` w przeciwnym razie.

### <a name="example"></a>Przykład

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="lockoperator"></a><a name="operator-inequality"></a>Lock:: operator! =

Operator nierówności.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Obiekt, który ma zostać porównany pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Zwraca `true`, jeśli `t` różni się od obiektu blokady, `false` w przeciwnym razie.

### <a name="example"></a>Przykład

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```
