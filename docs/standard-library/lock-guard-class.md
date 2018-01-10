---
title: "lock_guard — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs: C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c337d4188ccbc26280db59feab30ab7c11133bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lockguard-class"></a>lock_guard — Klasa
Reprezentuje szablon, który można wdrożyć do utworzenia obiektu, którego destruktora odblokowuje `mutex`.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Mutex>
class lock_guard;
```  
  
## <a name="remarks"></a>Uwagi  
 Argument szablonu `Mutex` nazwę *typu obiektu mutex*.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`lock_guard::mutex_type`|Synonim argumentu szablonu `Mutex`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[lock_guard](#lock_guard)|Konstruuje `lock_guard` obiektu.|  
|[lock_guard:: ~ lock_guard — destruktor](#dtorlock_guard_destructor)|Odblokowuje `mutex` przekazany do konstruktora.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<obiektu mutex >  
  
 **Namespace:** Standard  
  
##  <a name="lock_guard"></a>lock_guard::lock_guard — Konstruktor  
 Konstruuje `lock_guard` obiektu.  
  
```cpp  
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```  
  
### <a name="parameters"></a>Parametry  
 `Mtx`  
 A *typu obiektu mutex* obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor konstrukcji obiektu typu `lock_guard` i blokad `Mtx`. Jeśli `Mtx` nie jest mutex cykliczne, musi być odblokowany po wywołaniu tego konstruktora.  
  
 Drugi Konstruktor nie blokuje `Mtx`. `Mtx`musi być zablokowany, po wywołaniu tego konstruktora. Konstruktor zgłasza żadnych wyjątków.  
  
##  <a name="dtorlock_guard_destructor"></a>lock_guard:: ~ lock_guard — destruktor  
 Odblokowuje `mutex` przekazany do konstruktora.  
  
```
~lock_guard() noexcept;
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `mutex` nie istnieje po uruchomieniu destruktor zachowanie jest niezdefiniowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex >](../standard-library/mutex.md)



