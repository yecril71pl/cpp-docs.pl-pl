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
ms.openlocfilehash: be7a2b7bbac8affd0bc668113cac30f4bed96a6b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017298"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock — Metoda
Czeka, aż do bieżącego obiektu lub **semafora** obiekt skojarzony z określone dojście jest w stanie sygnałowego lub przed upływem określonego limitu czasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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