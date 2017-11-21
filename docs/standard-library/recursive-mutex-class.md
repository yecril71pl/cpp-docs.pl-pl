---
title: "recursive_mutex — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
dev_langs: C++
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 5d2567c5ced5b42dc40529a07535458e9fe34d75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recursivemutex-class"></a>recursive_mutex — Klasa
Reprezentuje *typu obiektu mutex*. Contrast do [obiektu mutex](../standard-library/mutex-class-stl.md), zachowanie wywołania metod blokowania dla obiektów, które są już zablokowane jest dobrze zdefiniowany.  
  
## <a name="syntax"></a>Składnia  
  
```
class recursive_mutex;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[recursive_mutex](#recursive_mutex)|Konstruuje `recursive_mutex` obiektu.|  
|[~ recursive_mutex — destruktor](#dtorrecursive_mutex_destructor)|Zwalnia wszystkie zasoby, które są używane przez `recursive_mutex` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[blokady](#lock)|Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności obiektu mutex.|  
|[try_lock](#try_lock)|Próbuje uzyskać prawo własności obiektu mutex bez blokowania.|  
|[odblokowywanie](#unlock)|Zwalnia prawo własności obiektu mutex.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<obiektu mutex >  
  
 **Namespace:** Standard  
  
##  <a name="lock"></a>blokady  
 Wątek wywołujący blokuje, dopóki wątek uzyskuje prawo własności do `mutex`.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, metoda zwraca natychmiast i poprzednia blokada będzie obowiązywać.  
  
##  <a name="recursive_mutex"></a>recursive_mutex  
 Konstruuje `recursive_mutex` obiekt, który nie jest zablokowany.  
  
```cpp  
recursive_mutex();
```  
  
##  <a name="dtorrecursive_mutex_destructor"></a>~ recursive_mutex  
 Zwalnia wszystkie zasoby, które są używane przez obiekt.  
  
```cpp  
~recursive_mutex();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest zablokowany, po uruchomieniu destruktor, zachowanie jest niezdefiniowany.  
  
##  <a name="try_lock"></a>try_lock  
 Próbuje uzyskać prawo własności `mutex` bez blokowania.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli metoda pomyślnie uzyskuje prawo własności `mutex` lub jeśli wątek wywołujący już właścicielem `mutex`; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wątek wywołujący już właścicielem `mutex`, funkcja natychmiast zwraca `true`, i obowiązuje poprzedniej blokady.  
  
##  <a name="unlock"></a>odblokowywanie  
 Zwalnia prawo własności obiektu mutex.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwalnia własność `mutex` tylko wtedy, gdy jest ona wywoływana tyle razy, ile [blokady](#lock) i [try_lock](#try_lock) pomyślnie wywołana dla `recursive_mutex` obiektu.  
  
 Jeśli wątek wywołujący nie jest właścicielem `mutex`, zachowanie jest niezdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex >](../standard-library/mutex.md)



