---
title: "Lock::operator — wartość logiczna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- operator bool
- msclr.lock.operator bool
- lock.operator bool
- msclr::lock::operator bool
- lock::operator bool
dev_langs: C++
helpviewer_keywords: lock::operator bool
ms.assetid: 007f0372-f812-4f1e-ba43-2584bd96eb11
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b797057679a1d0613936ae00bc8f76d32febd17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="lockoperator-bool"></a>lock::operator — wartość logiczna
Operator przy użyciu `lock` w wyrażeniu warunkowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
operator bool();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli blokada jest używana, `false` inaczej.  
  
## <a name="remarks"></a>Uwagi  
 Ten operator faktycznie konwertuje `_detail_class::_safe_bool` co jest bezpieczniejszy niż `bool` , ponieważ nie można przekonwertować na typ całkowity.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użycie pojedynczego wystąpienia klasy przez wiele wątków.  Klasy używa blokady na samym sobie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku.  Wątku głównego aplikacji nawiązywał blokady dla tego samego wystąpienia klasy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieje i czeka, aby wyjść do wszystkich wątków zakończył ich zadań.  
  
```  
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
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie Lock](../dotnet/lock-members.md)   
 [Lock::is_locked](../dotnet/lock-is-locked.md)