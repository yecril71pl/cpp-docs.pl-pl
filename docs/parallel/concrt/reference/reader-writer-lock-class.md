---
title: reader_writer_lock, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 81acced9d3df85cd12c8306aed530728edf17e15
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106225"
---
# <a name="readerwriterlock-class"></a>reader_writer_lock — Klasa
Składnik zapisywania preferencji oparte na kolejce czytnika-blokadę przy użyciu lokalnej tylko obrotowych. Blokady przyznaje najpierw w — najpierw out (FIFO) dostęp do składników zapisywania i starves czytelnicy obciążeniem ciągłe składników zapisywania.  
  
## <a name="syntax"></a>Składnia  
  
```
class reader_writer_lock;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-classes"></a>Publiczne klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[reader_writer_lock::scoped_lock — klasa](#scoped_lock_class)|Wyjątek bezpieczne otoka RAII, który może służyć do uzyskania `reader_writer_lock` blokowanie obiektów jako edytor.|  
|[reader_writer_lock::scoped_lock_read — klasa](#scoped_lock_read_class)|Wyjątek bezpieczne otoka RAII, który może służyć do uzyskania `reader_writer_lock` zablokować obiekty do odczytu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[reader_writer_lock](#ctor)|Tworzy nowy `reader_writer_lock` obiektu.|  
|[~ reader_writer_lock — destruktor](#dtor)|Niszczy `reader_writer_lock` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[lock](#lock)|Uzyskuje blokadę czytnika jako edytor.|  
|[lock_read](#lock_read)|Uzyskuje blokadę czytnik do odczytu. W przypadku modułów zapisujących active czytelnicy musiały czekać na ukończenie to wszystko. Czytnik po prostu rejestruje zainteresowanie blokady i czeka na składników zapisywania do jego zwolnienia.|  
|[try_lock —](#try_lock)|Próbuje uzyskać blokadę czytnika jako edytor bez blokowania.|  
|[try_lock_read](#try_lock_read)|Próbuje uzyskać blokadę czytnik do odczytu bez blokowania.|  
|[unlock](#unlock)|Odblokowuje czytnika blokadę oparte na zablokowane kto go czytnik lub składnika zapisywania.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `reader_writer_lock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="lock"></a> Blokady 

 Uzyskuje blokadę czytnika jako edytor.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Często jest to bezpieczniejsze korzystanie z [scoped_lock](#scoped_lock_class) konstrukcji nabywania i zwolnij `reader_writer_lock` obiektu jako edytor wyjątek bezpieczny sposób.  
  
 Po Edytor próbuje uzyskać blokady, wszystkie przyszłe czytelnicy blokuje aż moduły zapisujące zostały pomyślnie uzyskano i ogólnie blokady. Ta blokada jest ukierunkowane autorzy i może zablokować czytelnicy obciążeniem ciągłe składników zapisywania.  
  
 Moduły zapisujące są powiązane, tak, aby moduł zapisujący blokady zamykania zwalnia następny składnik zapisywania w wierszu.  
  
 Jeśli blokada jest już używana przez kontekst wywołania [improper_lock —](improper-lock-class.md) zostanie zgłoszony wyjątek.  
  
##  <a name="lock_read"></a> lock_read — 

 Uzyskuje blokadę czytnik do odczytu. W przypadku modułów zapisujących active czytelnicy musiały czekać na ukończenie to wszystko. Czytnik po prostu rejestruje zainteresowanie blokady i czeka na składników zapisywania do jego zwolnienia.  
  
```
void lock_read();
```  
  
### <a name="remarks"></a>Uwagi  
 Często jest to bezpieczniejsze korzystanie z [scoped_lock_read —](#scoped_lock_read_class) konstrukcji nabywania i zwolnij `reader_writer_lock` obiektu do odczytu w wyjątek bezpieczny sposób.  
  
 W przypadku modułów zapisujących, oczekiwanie na blokadę czytnik czeka na zakończenie wszystkich modułów zapisywania w wierszu zainstalowana nabyte, a blokady. Ta blokada jest ukierunkowane autorzy i może zablokować czytelnicy obciążeniem ciągłe składników zapisywania.  
  
##  <a name="ctor"></a> reader_writer_lock 

 Tworzy nowy `reader_writer_lock` obiektu.  
  
```
reader_writer_lock();
```  
  
##  <a name="dtor"></a> ~ reader_writer_lock 

 Niszczy `reader_writer_lock` obiektu.  
  
```
~reader_writer_lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Oczekuje się, że blokada nie jest już przechowywany po uruchomieniu destruktora. Nadal umożliwiając blokadę zapisu czytnik do niszczenia przy użyciu blokady przechowywane wyniki w niezdefiniowane zachowanie.  
  
##  <a name="scoped_lock_class"></a>  reader_writer_lock::scoped_lock — klasa  
 Wyjątek bezpieczne otoka RAII, który może służyć do uzyskania `reader_writer_lock` blokowanie obiektów jako edytor.  
  
```
class scoped_lock;
``` 
## <a name="scoped_lock_ctor"></a> scoped_lock::scoped_lock 

Konstruuje `scoped_lock` obiektu i uzyskuje `reader_writer_lock` obiekt przekazany w `_Reader_writer_lock` parametru jako edytor. Jeśli blokada jest używana przez inny wątek, to wywołanie spowoduje zablokowanie.  
  
  
```
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
*_Reader_writer_lock*<br/>
`reader_writer_lock` Obiektu do uzyskania jako edytor.  
  
## <a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock 

Niszczy `reader_writer_lock` obiektu i zwalnia blokadę podana w jego konstruktorze.   

```
~scoped_lock();
```  
  
##  <a name="scoped_lock_read_class"></a>  reader_writer_lock::scoped_lock_read — klasa  
 Wyjątek bezpieczne otoka RAII, który może służyć do uzyskania `reader_writer_lock` zablokować obiekty do odczytu.  
  
```
class scoped_lock_read;
```  
  
##  <a name="try_lock"></a> try_lock — 

 Próbuje uzyskać blokadę czytnika jako edytor bez blokowania.  

## <a name="scoped_lock_read_ctor"></a> scoped_lock_read::scoped_lock_read 

Konstruuje `scoped_lock_read` obiektu i uzyskuje `reader_writer_lock` obiekt przekazany w `_Reader_writer_lock` parametru do odczytu. Jeśli blokada jest używana przez inny wątek jako moduł zapisujący lub istnieją oczekujące modułów zapisujących, to wywołanie spowoduje zablokowanie.  
  
```
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```  
  
#### <a name="parameters"></a>Parametry  
*_Reader_writer_lock*<br/>
`reader_writer_lock` Obiektu można uzyskać do odczytu.  
  
## <a name="a-namescopedlockreaddtor--readerwriterlockscopedlockreadscopedlockread-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock::scoped_lock_read:: ~ scoped_lock_read — destruktor
Niszczy `scoped_lock_read` obiektu i zwalnia blokadę podana w jego konstruktorze.  

```
~scoped_lock_read();
```  
  
## <a name="try_lock"></a> try_lock — 

```
bool try_lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli blokada została uzyskana, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="try_lock_read"></a> try_lock_read — 

 Próbuje uzyskać blokadę czytnik do odczytu bez blokowania.  
  
```
bool try_lock_read();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli blokada została uzyskana, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="unlock"></a> Odblokowywanie 

 Odblokowuje czytnika blokadę oparte na zablokowane kto go czytnik lub składnika zapisywania.  
  
```
void unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 W przypadku modułów zapisujących, oczekiwanie na blokadę wersji blokady zawsze przejdzie do następnego składnika zapisywania w kolejności FIFO. Ta blokada jest ukierunkowane autorzy i może zablokować czytelnicy obciążeniem ciągłe składników zapisywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [critical_section, klasa](critical-section-class.md)
