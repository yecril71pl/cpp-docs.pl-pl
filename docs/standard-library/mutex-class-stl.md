---
title: "mutex — klasa (standardowa biblioteka C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
dev_langs: C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 37a6d72ab7f79c24606a5ffb0dcafe1e6c6d1e18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mutex-class-c-standard-library"></a>mutex — klasa (standardowa biblioteka C++)
Reprezentuje *typu obiektu mutex*. Obiekty tego typu może służyć do wymuszania wzajemne wykluczenie w programie.  
  
## <a name="syntax"></a>Składnia  
  
```
class mutex;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[mutex](#mutex)|Konstruuje `mutex` obiektu.|  
|[mutex:: ~ mutex — destruktor](#dtormutex_destructor)|Zwalnia wszystkie zasoby, które były używane przez `mutex` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[blokady](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.|  
|[native_handle](#native_handle)|Zwraca typ konkretnej implementacji, który reprezentuje dojście obiektu mutex.|  
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności `mutex` bez blokowania.|  
|[odblokowywanie](#unlock)|Zwalnia własność `mutex`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<obiektu mutex >  
  
 **Namespace:** Standard  
  
##  <a name="lock"></a>mutex::Lock
 Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="mutex"></a>mutex::mutex — Konstruktor  
 Konstruuje `mutex` obiekt, który nie jest zablokowany.  
  
```cpp  
constexpr mutex() noexcept;
```  
  
##  <a name="dtormutex_destructor"></a>mutex:: ~ mutex — destruktor  
 Zwalnia wszystkie zasoby, które są używane przez `mutex` obiektu.  
  
```cpp  
~mutex();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.  
  
##  <a name="native_handle"></a>mutex::native_handle
 Zwraca typ konkretnej implementacji, który reprezentuje dojście obiektu mutex. Dojście obiektu mutex można w sposób konkretnej implementacji.  
  
```
native_handle_type native_handle();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `native_handle_type`nie zdefiniowano jako `Concurrency::critical_section *` który jest rzutowany jako `void *`.  
  
##  <a name="try_lock"></a>mutex::try_lock
 Próbuje uzyskać prawo własności `mutex` bez blokowania.  
  
```cpp  
bool try_lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli metoda pomyślnie uzyskuje prawo własności `mutex`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
##  <a name="unlock"></a>mutex::Unlock
 Zwalnia własność `mutex`.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex >](../standard-library/mutex.md)



