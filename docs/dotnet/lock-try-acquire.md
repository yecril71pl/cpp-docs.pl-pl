---
title: Lock::try_acquire | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- try_acquire
- lock.try_acquire
- msclr.lock.try_acquire
- lock::try_acquire
- msclr::lock::try_acquire
dev_langs:
- C++
helpviewer_keywords:
- lock::try_acquire
ms.assetid: ef0649a9-e611-4495-84bd-2784533221d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25b5ec1ab7bb5c429538f312ee3b598d3d1d83ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="locktryacquire"></a>lock::try_acquire
Uzyskuje blokadę dla obiektu, określoną ilość czasu oczekiwania i zwracanie `bool` umożliwiające komunikowanie powodzenia nabycia zamiast generowania wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool try_acquire(  
   int _timeout_ms  
);  
bool try_acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_timeout`  
 Wartość limitu czasu (w milisekundach) lub jako <xref:System.TimeSpan>.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli uzyskano blokady, `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli już uzyskano blokady, ta funkcja nie działa.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użycie pojedynczego wystąpienia klasy przez wiele wątków.  Klasy używa blokady na samym sobie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku.  Wątku głównego aplikacji nawiązywał blokady dla tego samego wystąpienia klasy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieje i czeka, aby wyjść do wszystkich wątków zakończył ich zadań.  
  
```  
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
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie Lock](../dotnet/lock-members.md)   
 [lock::acquire](../dotnet/lock-acquire.md)