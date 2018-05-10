---
title: SRWLock::TryLockExclusive — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1cc9ee8a63d7403c3de408c924eeab07f1d0efa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive — Metoda
Próby uzyskania obiektu srwlock — w trybie wyłączności dla bieżącego lub określonego obiektu srwlock —. Jeśli połączenie zostanie nawiązane, wątek wywołujący przejmuje blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lock`  
 Wskaźnik do obiektu srwlock —.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia obiektu srwlock — w trybie wyłączności i wątku wywołującym ma na własność blokady. W przeciwnym razie srwlock — obiekt, którego stan jest nieprawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [SRWLock, klasa](../windows/srwlock-class.md)