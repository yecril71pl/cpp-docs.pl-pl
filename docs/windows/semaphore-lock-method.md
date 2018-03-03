---
title: "Semaphore::Lock — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11531a07f161722947d03a53392b8315b7593958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="semaphorelock-method"></a>Semaphore::Lock — Metoda
Czeka, aż do bieżącego obiektu lub obiektu semafora skojarzonego z określonego dojścia jest w stanie sygnałowego lub przed upływem określonego limitu czasu.  
  
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
 Dojście do obiektu semafora.  
  
## <a name="return-value"></a>Wartość zwracana  
 Details::SyncLockWithStatusT\<HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
[Semaphore, klasa](../windows/semaphore-class.md)
 