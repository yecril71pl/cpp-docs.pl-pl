---
title: Semaphore::Lock, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39f2fe48b1e7a1a7c6b875b988d861d5fb48698a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642149"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock — Metoda
Czeka, aż do bieżącego obiektu lub **semafora** obiekt skojarzony z określone dojście jest w stanie sygnałowego lub przed upływem określonego limitu czasu.  
  
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
  
### <a name="parameters"></a>Parametry  
 *MS*  
 Interwał limitu czasu w milisekundach. Wartość domyślna to NIESKOŃCZONE, który oczekuje w nieskończoność.  
  
 *h*  
 Dojście do **semafora** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 A `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Semaphore, klasa](../windows/semaphore-class.md)