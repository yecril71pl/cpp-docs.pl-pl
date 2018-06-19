---
title: Lock::Lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
dev_langs:
- C++
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: df35eed8711e83174316ac9912f7ba535ef9ebf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135030"
---
# <a name="locklock"></a>lock::lock
Konstruuje `lock` obiektu opcjonalnie oczekiwania na uzyskanie blokady w nieskończoność, na określony czas lub wcale.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `_object`  
 Obiekt do zablokowania.  
  
 `_timeout`  
 Wartość limitu czasu (w milisekundach) lub jako <xref:System.TimeSpan>.  
  
## <a name="exceptions"></a>Wyjątki  
 Zgłasza wyjątek <xref:System.ApplicationException> Jeśli przejęcie blokady nie występuje przed upływem limitu czasu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwsze trzy rodzaje konstruktora próby uzyskania blokady na `_object` przed upływem określonego limitu czasu (lub <xref:System.Threading.Timeout.Infinite> Jeśli nie zostanie określona).  
  
 Czwarty formularza konstruktora nie uzyskania blokady na `_object`. `lock_later` jest elementem członkowskim [wyliczenie lock_when](../dotnet/lock-when-enum.md). Użyj [lock::acquire](../dotnet/lock-acquire.md) lub [lock::try_acquire](../dotnet/lock-try-acquire.md) na przejęcie blokady w takim przypadku.  
  
 Zablokuj automatycznie zostanie wydana wywołanego destruktor.  
  
 `_object` nie może być <xref:System.Threading.ReaderWriterLock>.  Jeśli tak jest, wystąpi błąd kompilatora.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użycie pojedynczego wystąpienia klasy przez wiele wątków.  Klasy używa blokady na samym sobie, aby upewnić się, że dostęp do swoich danych wewnętrznych są spójne dla każdego wątku.  Wątku głównego aplikacji nawiązywał blokady dla tego samego wystąpienia klasy okresowo sprawdzać, czy wszystkie wątki robocze nadal istnieje i czeka, aby wyjść do wszystkich wątków zakończył ich zadań.  
  
```  
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
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [elementy członkowskie Lock](../dotnet/lock-members.md)   
 [Zablokuj:: ~ lock](../dotnet/lock-tilde-lock.md)   
 [Lock::Acquire](../dotnet/lock-acquire.md)   
 [lock::try_acquire](../dotnet/lock-try-acquire.md)