---
title: Semaphore::Lock — Metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 80b4db212236da6c9fb320ff5a5e04f4e9f4a4c6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892478"
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
 