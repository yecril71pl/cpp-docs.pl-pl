---
title: critical_section — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- critical_section
- CONCRT/concurrency::critical_section
- CONCRT/concurrency::critical_section::critical_section::scoped_lock Class
- CONCRT/concurrency::critical_section::critical_section
- CONCRT/concurrency::critical_section::lock
- CONCRT/concurrency::critical_section::native_handle
- CONCRT/concurrency::critical_section::try_lock
- CONCRT/concurrency::critical_section::try_lock_for
- CONCRT/concurrency::critical_section::unlock
dev_langs:
- C++
helpviewer_keywords:
- critical_section class
ms.assetid: fa3c89d6-be5d-4d1b-bddb-8232814e6cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0287c74155e7b4fe827bb015b43cfca3384f3b1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693565"
---
# <a name="criticalsection-class"></a>critical_section — Klasa
Mutex nie obsługującą, która jawnie rozpoznaje współbieżności środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```
class critical_section;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`native_handle_type`|Odwołanie do `critical_section` obiektu.|  
  
### <a name="public-classes"></a>Klas publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[critical_section::scoped_lock — klasa](#critical_section__scoped_lock_class)|Bezpieczne wyjątek RAII otoki dla `critical_section` obiektu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[critical_section](#ctor)|Tworzy nową sekcję krytyczne.|  
|[~ critical_section — destruktor](#dtor)|Niszczy sekcja krytyczna.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[lock](#lock)|Uzyskuje w tej sekcji krytycznych.|  
|[native_handle](#native_handle)|Zwraca określonego uchwyt macierzysty platformy, jeśli taka istnieje.|  
|[try_lock](#try_lock)|Próbuje uzyskać blokady bez blokowania.|  
|[try_lock_for](#try_lock_for)|Próbuje uzyskać blokady bez blokowania określoną liczbę milisekund.|  
|[unlock](#unlock)|Umożliwia odblokowanie sekcji krytycznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [struktury danych synchronizacji](../../../parallel/concrt/synchronization-data-structures.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `critical_section`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> critical_section 

 Tworzy nową sekcję krytyczne.  
  
```
critical_section();
```  
  
##  <a name="dtor"></a> ~ critical_section 

 Niszczy sekcja krytyczna.  
  
```
~critical_section();
```  
  
### <a name="remarks"></a>Uwagi  
 Oczekuje się, że blokada nie jest już przechowywany po uruchomieniu destruktor. Nadal stosowanie sekcja krytyczna do destruct z blokadą przechowywać wyniki w formacie niezdefiniowane zachowanie.  
  
##  <a name="lock"></a> blokady 

 Uzyskuje w tej sekcji krytycznych.  
  
```
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Często jest korzystanie z bezpieczniejszych [scoped_lock](#critical_section__scoped_lock_class) konstrukcja pobierać i zwolnij `critical_section` obiektu wyjątek w bezpieczny sposób.  
  
 Jeśli blokada jest już używana przez kontekst wywołania [improper_lock —](improper-lock-class.md) zostanie wygenerowany wyjątek.  
  
##  <a name="native_handle"></a> native_handle 

 Zwraca określonego uchwyt macierzysty platformy, jeśli taka istnieje.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do sekcji krytycznych.  
  
### <a name="remarks"></a>Uwagi  
 A `critical_section` obiektu nie jest skojarzony z platform określonych uchwyt macierzysty dla systemu operacyjnego Windows. Metoda po prostu zwraca odwołanie do samego obiektu.  
  
##  <a name="critical_section__scoped_lock_class"></a>  critical_section::scoped_lock — klasa  
 Bezpieczne wyjątek RAII otoki dla `critical_section` obiektu.  
  
```
class scoped_lock;
```  
  
##  <a name="critical_section__scoped_lock_ctor"></a> scoped_lock::scoped_lock 

 Konstruuje `scoped_lock` obiektu i uzyskuje `critical_section` przekazano obiekt `_Critical_section` parametru. Jeśli sekcja krytyczna jest przechowywany przez inny wątek, blokuje to wywołanie.  
  
```
explicit _CRTIMP scoped_lock(critical_section& _Critical_section);
```  
  
### <a name="parameters"></a>Parametry  
 `_Critical_section`  
 Sekcja krytyczna do zablokowania.  
  
##  <a name="critical_section__scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock — 

 Niszczy `scoped_lock` obiektu i zwalnia sekcja krytyczna podana w jego konstruktora.  
  
```
~scoped_lock();
```  
  
##  <a name="try_lock"></a> try_lock 

 Próbuje uzyskać blokady bez blokowania.  
  
```
bool try_lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli uzyskano blokady, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="try_lock_for"></a> try_lock_for 

 Próbuje uzyskać blokady bez blokowania określoną liczbę milisekund.  
  
```
bool try_lock_for(unsigned int _Timeout);
```  
  
### <a name="parameters"></a>Parametry  
 `_Timeout`  
 Liczba milisekund oczekiwania przed przekroczeniem limitu czasu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli uzyskano blokady, wartość `true`; w przeciwnym razie wartość `false`.  
  
##  <a name="unlock"></a> odblokowywanie 

 Umożliwia odblokowanie sekcji krytycznych.  
  
```
void unlock();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)   
 [reader_writer_lock, klasa](reader-writer-lock-class.md)
