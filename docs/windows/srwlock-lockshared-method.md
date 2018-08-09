---
title: SRWLock::LockShared, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
dev_langs:
- C++
helpviewer_keywords:
- LockShared method
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dfc50ae0732471f8cb91b2c380d4c4772350f47
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652129"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared — Metoda
Uzyskuje **SRWLock** obiektu w tryb udostępniania.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *lock*  
 Wskaźnik do **SRWLock** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 **SRWLock** obiektu w tryb udostępniania.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [SRWLock, klasa](../windows/srwlock-class.md)