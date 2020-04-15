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
ms.openlocfilehash: ea09dd3d4a2eaf4cf7708d09509cfecfa4a6c6d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373075"
---
# <a name="lock-class"></a>Klasa lock

Ta klasa automatyzuje przy blokadzie do synchronizowania dostępu do obiektu z kilku wątków.  Po skonstruowaniu nabywa blokadę, a po zniszczeniu zwalnia blokadę.

## <a name="syntax"></a>Składnia

```cpp
ref class lock;
```

## <a name="remarks"></a>Uwagi

`lock`jest dostępna tylko dla obiektów CLR i może być używana tylko w kodzie CLR.

Wewnętrznie, lock klasy używa <xref:System.Threading.Monitor> do synchronizacji dostępu. Aby uzyskać więcej informacji, zobacz artykuł, do którego istnieje odwołanie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktorzy publiczni

|Nazwa|Opis|
|---------|-----------|
|[lock::lock](#lock)|Tworzy `lock` obiekt, opcjonalnie czeka na uzyskanie blokady na zawsze, przez określony czas lub w ogóle.|
|[blokada::~blokada](#tilde-lock)|Niszczy `lock` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|---------|-----------|
|[lock::acquire](#acquire)|Uzyskuje blokadę na obiekcie, opcjonalnie czekając na uzyskanie blokady na zawsze, przez określony czas lub wcale.|
|[lock::is_locked](#is-locked)|Wskazuje, czy blokada jest utrzymywana.|
|[lock::release](#release)|Zwalnia blokadę.|
|[lock::try_acquire](#try-acquire)|Uzyskuje blokadę na obiekcie, czekając na określoną ilość `bool` czasu i zwracając do raportu sukcesu nabycia zamiast zgłaszania wyjątku.|

### <a name="public-operators"></a>Operatorzy publiczni

|Nazwa|Opis|
|---------|-----------|
|[blokada::operator&nbsp;bool](#operator-bool)|Operator do `lock` używania w wyrażeniu warunkowym.|
|[lock::operator==](#operator-equality)|Operator równości.|
|[blokada::operator!=](#operator-inequality)|Operator nierówności.|

## <a name="requirements"></a>Wymagania

**Plik** \<nagłówka msclr\lock.h>

**Msclr przestrzeni nazw**

## <a name="locklock"></a><a name="lock"></a>blokada::blokada

Tworzy `lock` obiekt, opcjonalnie czeka na uzyskanie blokady na zawsze, przez określony czas lub w ogóle.

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
Obiekt, który ma zostać zablokowany.

*_timeout*<br/>
Wartość przesuwu czasu w <xref:System.TimeSpan>milisekundach lub jako .

### <a name="exceptions"></a>Wyjątki

Zgłasza, <xref:System.ApplicationException> jeśli nabycie blokady nie występuje przed przesuwem czasu.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formy konstruktora spróbuj uzyskać `_object` blokadę w określonym <xref:System.Threading.Timeout.Infinite> okresie limitu czasu (lub jeśli nie jest określony).

Czwarta forma konstruktora nie uzyskuje `_object`blokady na . `lock_later`jest członkiem [lock_when wyliczenia](../dotnet/lock-when-enum.md). Użyj [lock::acquire](../dotnet/lock-acquire.md) lub [lock::try_acquire,](../dotnet/lock-try-acquire.md) aby uzyskać blokadę w tym przypadku.

Blokada zostanie automatycznie zwolniona, gdy zostanie wywołana destruktor.

`_object`nie może <xref:System.Threading.ReaderWriterLock>być .  Jeśli tak jest, spowoduje błąd kompilatora.

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach. Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku. Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Aplikacja główna następnie czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="locklock"></a><a name="tilde-lock"></a>blokada::~blokada

Niszczy `lock` obiekt.

```cpp
~lock();
```

### <a name="remarks"></a>Uwagi

Destruktor wywołuje [blokadę::release](../dotnet/lock-release.md).

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach.  Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku.  Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Aplikacja główna następnie czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="lockacquire"></a><a name="acquire"></a>lock::acquire

Uzyskuje blokadę na obiekcie, opcjonalnie czekając na uzyskanie blokady na zawsze, przez określony czas lub wcale.

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
Wartość limitu czasu w milisekundach lub jako . <xref:System.TimeSpan>

### <a name="exceptions"></a>Wyjątki

Zgłasza, <xref:System.ApplicationException> jeśli nabycie blokady nie występuje przed przesuwem czasu.

### <a name="remarks"></a>Uwagi

Jeśli nie podano wartości limitu czasu, domyślny <xref:System.Threading.Timeout.Infinite>limit czasu to .

Jeśli blokada została już nabyta, ta funkcja nic nie robi.

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach.  Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku. Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Aplikacja główna następnie czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="lockis_locked"></a><a name="is-locked"></a>blokada::is_locked

Wskazuje, czy blokada jest utrzymywana.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Wartość zwracana

`true`jeśli blokada jest `false` utrzymywana, w przeciwnym razie.

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach.  Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku.  Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze i czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>blokada::operator bool

Operator do `lock` używania w wyrażeniu warunkowym.

```cpp
operator bool();
```

### <a name="return-value"></a>Wartość zwracana

`true`jeśli blokada jest `false` utrzymywana, w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ten operator faktycznie `_detail_class::_safe_bool` konwertuje `bool` do których jest bezpieczniejsze niż dlatego, że nie można przekonwertować na typ integralną.

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach.  Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku. Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Główna aplikacja czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="lockrelease"></a><a name="release"></a>blokada::release

Zwalnia blokadę.

```cpp
void release();
```

### <a name="remarks"></a>Uwagi

Jeśli blokada nie `release` jest utrzymywana, nic nie robi.

Nie musisz wywoływać tej funkcji jawnie. Gdy `lock` obiekt wykracza poza zakres, jego `release`destruktor wywołuje .

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach. Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku. Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Aplikacja główna następnie czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>blokada::try_acquire

Uzyskuje blokadę na obiekcie, czekając na określoną ilość `bool` czasu i zwracając do raportu sukcesu nabycia zamiast zgłaszania wyjątku.

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
Wartość limitu czasu w milisekundach lub jako . <xref:System.TimeSpan>

### <a name="return-value"></a>Wartość zwracana

`true`jeśli blokada `false` została nabyta, w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Jeśli blokada została już nabyta, ta funkcja nic nie robi.

### <a name="example"></a>Przykład

W tym przykładzie użyto pojedynczego wystąpienia klasy w kilku wątkach. Klasa używa blokady na siebie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku. Główny wątek aplikacji używa blokady na tym samym wystąpieniu klasy, aby okresowo sprawdzać, czy nadal istnieją wątki robocze. Aplikacja główna następnie czeka na zakończenie, dopóki wszystkie wątki robocze nie zakończą swoich zadań.

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

## <a name="lockoperator"></a><a name="operator-equality"></a>blokada::operator==

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

`true` Zwraca, `t` jeśli jest taki sam jak `false` obiekt blokady, w przeciwnym razie.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a>blokada::operator!=

Operator nierówności.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Obiekt do porównania dla nierówności.

### <a name="return-value"></a>Wartość zwracana

`true` Zwraca, `t` jeśli różni się od `false` obiektu blokady, w przeciwnym razie.

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
