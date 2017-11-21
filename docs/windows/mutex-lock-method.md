---
title: "Mutex::Lock — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs: C++
helpviewer_keywords: Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6940c69e61f25abf3880190f58d83a995e2c84e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mutexlock-method"></a>Mutex::Lock — Metoda
Czeka, aż do bieżącego obiektu lub obiektu Mutex skojarzonego z określonego dojścia zwalnia obiektu mutex lub przed upływem określonego limitu czasu.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `milliseconds`  
 Interwał limitu czasu w milisekundach. Wartość domyślna to bez ograniczeń czasowych, która oczekuje na nieograniczony czas.  
  
 `h`  
 Dojście obiektu Mutex.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —
 
 ## <a name="see-also"></a>Zobacz też
 [Mutex — klasa](../windows/mutex-class1.md)