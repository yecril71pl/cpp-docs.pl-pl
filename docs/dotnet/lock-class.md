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
ms.openlocfilehash: 43418da36aa2d87608a9d672e4345d24011be0b3
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805958"
---
# <a name="lock-class"></a>Klasa lock

Ta klasa umożliwia zautomatyzowanie biorąc blokady do synchronizowania dostępu do obiektu z kilku wątków.  Gdy konstruowany kupuje blokady i kiedy niszczony jego wersji blokady.

## <a name="syntax"></a>Składnia

```cpp
ref class lock;
```

## <a name="remarks"></a>Uwagi

`lock` jest dostępna tylko w przypadku obiektów CLR i można używać tylko w kodzie CLR.

Wewnętrznie używa klasy blokady <xref:System.Threading.Monitor> do synchronizowania dostępu. Aby uzyskać więcej informacji zobacz ów artykuł.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|---------|-----------|
|[lock::lock](#lock)|Konstruuje `lock` obiektu, opcjonalnie oczekiwania na uzyskanie blokady w nieskończoność, przez określony przedział czasu, lub wcale.|
|[lock::~lock](#tilde-lock)|Destructs `lock` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|---------|-----------|
|[lock::acquire](#acquire)|Uzyskuje blokadę na obiekcie opcjonalnie oczekiwania na uzyskanie blokady w nieskończoność, przez określony przedział czasu, lub wcale.|
|[lock::is_locked](#is-locked)|Wskazuje, czy blokada jest zablokowany.|
|[lock::release](#release)|Zwalnia blokadę.|
|[lock::try_acquire](#try-acquire)|Uzyskaj blokadę na obiekcie oczekiwanie na określoną ilość czasu i zwracanie `bool` do raportują Powodzenie przejęcia, zamiast zgłaszać wyjątek.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|---------|-----------|
|[Lock::operator, wartość&nbsp;bool](#operator-bool)|Operator przy użyciu `lock` w wyrażeniu warunkowym.|
|[lock::operator==](#operator-equality)|Operator równości.|
|[lock::operator!=](#operator-inequality)|Operator nierówności.|

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\lock.h >

**Namespace** msclr



## <a name="lock"></a>Lock::Lock

Konstruuje `lock` obiektu, opcjonalnie oczekiwania na uzyskanie blokady w nieskończoność, przez określony przedział czasu, lub wcale.

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

*_obiekt*<br/>
Obiekt do zablokowania.

*_limit czasu*<br/>
Wartość limitu czasu (w milisekundach) lub jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Wyjątki

Zgłasza <xref:System.ApplicationException> Jeśli pozyskiwania blokady nie występuje przed upływem limitu czasu.

### <a name="remarks"></a>Uwagi

Pierwsze trzy rodzaje konstruktora próbuje uzyskać blokadę na `_object` przed upływem limitu czasu określonego (lub <xref:System.Threading.Timeout.Infinite> Jeśli nie określono).

Czwarty formularza Konstruktor nie uzyskać blokadę na `_object`. `lock_later` jest elementem członkowskim [lock_when — wyliczenie](../dotnet/lock-when-enum.md). Użyj [lock::acquire](../dotnet/lock-acquire.md) lub [lock::try_acquire](../dotnet/lock-try-acquire.md) można uzyskać blokady w tym przypadku.

Zablokuj automatycznie zostaną wydane po wywołaniu destruktora.

`_object` nie może być <xref:System.Threading.ReaderWriterLock>.  Jeśli tak jest, powoduje błąd kompilatora.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach. Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku. Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Głównej aplikacji czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="tilde-lock"></a>Zablokuj:: ~ lock

Destructs `lock` obiektu.

```cpp
~lock();
```

### <a name="remarks"></a>Uwagi

Wywołania destruktora [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach.  Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku.  Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Głównej aplikacji czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="acquire"></a>Lock::Acquire

Uzyskuje blokadę na obiekcie opcjonalnie oczekiwania na uzyskanie blokady w nieskończoność, przez określony przedział czasu, lub wcale.

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

*_limit czasu*<br/>
Wartość limitu czasu (w milisekundach) lub jako <xref:System.TimeSpan>.

### <a name="exceptions"></a>Wyjątki

Zgłasza <xref:System.ApplicationException> Jeśli pozyskiwania blokady nie występuje przed upływem limitu czasu.

### <a name="remarks"></a>Uwagi

Jeśli wartość limitu czasu nie jest podany, domyślny limit czasu wynosi <xref:System.Threading.Timeout.Infinite>.

Jeśli już pozyskany blokadę, ta funkcja nie działa.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach.  Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku. Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Głównej aplikacji czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="is-locked"></a>Lock::is_locked

Wskazuje, czy blokada jest zablokowany.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli blokada jest używana, `false` inaczej.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach.  Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku.  Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy mogą okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieje, i czeka, aby zakończyć pracę, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="operator-bool"></a>Lock::operator, wartość logiczna

Operator przy użyciu `lock` w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli blokada jest używana, `false` inaczej.

### <a name="remarks"></a>Uwagi

Ten operator faktycznie konwertuje `_detail_class::_safe_bool` co jest bezpieczniejszy niż `bool` , ponieważ nie można przekonwertować na typ całkowitoliczbowy.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach.  Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku. Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Aplikacji głównej czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="release"></a>Lock::Release

Zwalnia blokadę.

```cpp
void release();
```

### <a name="remarks"></a>Uwagi

Jeśli blokada nie jest zablokowany, `release` nic nie robi.

Nie trzeba jawnie wywołać tę funkcję. Gdy `lock` obiekt wykracza poza zakres, jego wywołania destruktora `release`.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach. Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku. Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Głównej aplikacji czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="try-acquire"></a>Lock::try_acquire

Uzyskaj blokadę na obiekcie oczekiwanie na określoną ilość czasu i zwracanie `bool` do raportują Powodzenie przejęcia, zamiast zgłaszać wyjątek.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Parametry

*_limit czasu*<br/>
Wartość limitu czasu (w milisekundach) lub jako <xref:System.TimeSpan>.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli blokada została uzyskana, `false` inaczej.

### <a name="remarks"></a>Uwagi

Jeśli już pozyskany blokadę, ta funkcja nie działa.

### <a name="example"></a>Przykład

W tym przykładzie użycie pojedynczego wystąpienia klasy w wielu wątkach. Klasa stosowana jest blokada na siebie, aby upewnić się, że dostęp do jego wewnętrznych danych są spójne dla każdego wątku. Głównego wątku aplikacji stosowana jest blokada na tym samym wystąpieniu klasy, należy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieją. Głównej aplikacji czeka, dopóki wszystkie wątki robocze zostały wykonane ich zadań.

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

## <a name="operator-equality"></a>Lock::operator, wartość ==

Operator równości.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Obiekt do porównania dla równości.

### <a name="return-value"></a>Wartość zwracana

Zwraca `true` Jeśli `t` jest taka sama jak obiektu blokady `false` inaczej.

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

## <a name="operator-inequality"></a>Lock::operator, wartość! =

Operator nierówności.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Obiekt do porównania pod kątem nierówności.

### <a name="return-value"></a>Wartość zwracana

Zwraca `true` Jeśli `t` różni się od obiektu blokady `false` inaczej.

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