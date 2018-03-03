---
title: "SRWLock::TryLockShared — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c36657b5c732055260dc77471e109961a66c144
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared — Metoda
Próby uzyskania obiektu srwlock — w trybie udostępniania dla bieżącego lub określonego obiektu srwlock —.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lock`  
 Wskaźnik do obiektu srwlock —.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia obiektu srwlock — w trybie udostępniania i wątku wywołującym ma na własność blokady. W przeciwnym razie srwlock — obiekt, którego stan jest nieprawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [SRWLock, klasa](../windows/srwlock-class.md)