---
title: Klasa reader_writer_lock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
dev_langs:
- C++
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a2f48a80efca0ec6e85a315b355a6482fb2096b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="readerwriterlock-class"></a>reader_writer_lock — Klasa
Składnik zapisywania — preferencji na podstawie kolejki czytnika-blokadę wirowania tylko lokalnie. Blokada najpierw przyznaje - najpierw out (FIFO) dostępu do zapisywania i starves czytników obciążenie ciągłego składników zapisywania.  
  
## <a name="syntax"></a>Składnia  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-classes"></a>Klas publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[reader_writer_lock::scoped_lock — klasa](#scoped_lock_class)|Wyjątek bezpieczne RAII otoki używany do uzyskania `reader_writer_lock` zablokować obiekty jako edytor.|  
|[reader_writer_lock::scoped_lock_read — klasa](#scoped_lock_read_class)|Wyjątek bezpieczne RAII otoki używany do uzyskania `reader_writer_lock` zablokować obiekty do odczytu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|Tworzy nową `reader_writer_lock` obiektu.|  
|[~ reader_writer_lock — destruktor](#dtor)|Niszczy `reader_writer_lock` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[lock](#lock)|Uzyskuje blokadę czytnika jako edytor.|  
|[lock_read](#lock_read)|Uzyskuje blokadę czytnik do odczytu. W przypadku zapisywania active czytników trzeba poczekaj na wykonanie zadania. Czytnik po prostu rejestruje zainteresowanie blokady i czeka na składników zapisywania do jego zwolnienia.|  
|[try_lock](#try_lock)|Próbuje uzyskać blokadę czytnika jako edytor bez blokowania.|  
|[try_lock_read](#try_lock_read)|Próbuje uzyskać blokadę czytnik do odczytu bez blokowania.|  
|[unlock](#unlock)|Umożliwia odblokowanie czytnika blokadę oparte na zablokowany kto go czytnik lub składnika zapisywania.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `reader_writer_lock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="lock"></a> blokady 

 Uzyskuje blokadę czytnika jako edytor.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Często jest korzystanie z bezpieczniejszych [scoped_lock](#scoped_lock_class) konstrukcja pobierać i zwolnij `reader_writer_lock` obiektu jako składnik zapisywania wyjątek w bezpieczny sposób.  
  
 Po Edytor próbuje uzyskać blokady, wszystkie przyszłe czytników zablokuje aż do zapisywania pomyślnie nabyte i zwolnione blokady. Ta blokada jest ukierunkowane pod kątem autorzy i można blokować go, czytników obciążenie ciągłego składników zapisywania.  
  
 Autorzy są powiązane łańcuchem zależności, aby moduł zapisujący blokady Kończenie zwalnia twórcę dalej w wierszu.  
  
 Jeśli blokada jest już używana przez kontekst wywołania [improper_lock —](improper-lock-class.md) zostanie wygenerowany wyjątek.  
  
##  <a name="lock_read"></a> lock_read 

 Uzyskuje blokadę czytnik do odczytu. W przypadku zapisywania active czytników trzeba poczekaj na wykonanie zadania. Czytnik po prostu rejestruje zainteresowanie blokady i czeka na składników zapisywania do jego zwolnienia.  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>Uwagi  
 Często jest korzystanie z bezpieczniejszych [scoped_lock_read](#scoped_lock_read_class) konstrukcja pobierać i zwolnij `reader_writer_lock` obiektu do odczytu wyjątek w bezpieczny sposób.  
  
 W przypadku zapisywania oczekiwania na blokadę czytnik będzie czekać dopóki wszystkie składniki zapisywania w wierszu zostały nabyte i zwolnione blokady. Ta blokada jest ukierunkowane pod kątem autorzy i można blokować go, czytników obciążenie ciągłego składników zapisywania.  
  
##  <a name="ctor"></a> reader_writer_lock 

 Tworzy nową `reader_writer_lock` obiektu.  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a> ~ reader_writer_lock 

 Niszczy `reader_writer_lock` obiektu.  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Oczekuje się, że blokada nie jest już przechowywany po uruchomieniu destruktor. Nadal stosowanie czytnika blokadę zapisu do destruct z blokadą przechowywać wyniki w formacie niezdefiniowane zachowanie.  
  
##  <a name="scoped_lock_class"></a>  reader_writer_lock::scoped_lock — klasa  
 Wyjątek bezpieczne RAII otoki używany do uzyskania `reader_writer_lock` zablokować obiekty jako edytor.  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock 

Konstruuje `scoped_lock` obiektu i uzyskuje `reader_writer_lock` przekazano obiekt `_Reader_writer_lock` parametr jako edytor. Jeśli blokada jest używana przez inny wątek, blokuje to wywołanie.  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
 `_Reader_writer_lock`  
 `reader_writer_lock` Obiekt, aby uzyskać jak edytor.  
  
## <a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock — 

Niszczy `reader_writer_lock` obiektu i zwalnia blokadę podana w jego konstruktora.   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>  reader_writer_lock::scoped_lock_read — klasa  
 Wyjątek bezpieczne RAII otoki używany do uzyskania `reader_writer_lock` zablokować obiekty do odczytu.  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a> try_lock 

 Próbuje uzyskać blokadę czytnika jako edytor bez blokowania.  

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read 

Konstruuje `scoped_lock_read` obiektu i uzyskuje `reader_writer_lock` przekazano obiekt `_Reader_writer_lock` parametru do odczytu. Jeśli istnieją oczekujące autorów blokada jest używana przez inny wątek jako edytor, blokuje to wywołanie.  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
 `_Reader_writer_lock`  
 `reader_writer_lock` Obiektu do uzyskania dostępu do odczytu.  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock::scoped_lock_read:: ~ scoped_lock_read — destruktor
Niszczy `scoped_lock_read` obiektu i zwalnia blokadę podana w jego konstruktora.  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a> try_lock 

```
bool try_lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli uzyskano blokady, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="try_lock_read"></a> try_lock_read 

 Próbuje uzyskać blokadę czytnik do odczytu bez blokowania.  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli uzyskano blokady, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="unlock"></a> odblokowywanie 

 Umożliwia odblokowanie czytnika blokadę oparte na zablokowany kto go czytnik lub składnika zapisywania.  
  
```
void unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku zapisywania oczekiwania na blokadę wersji blokady zawsze przejdzie do następnego składnika zapisywania w kolejności FIFO. Ta blokada jest ukierunkowane pod kątem autorzy i można blokować go, czytników obciążenie ciągłego składników zapisywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [critical_section, klasa](critical-section-class.md)
