---
title: "SRWLock::TryLockExclusive — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs: C++
helpviewer_keywords: TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a23629ae5bc7d1645367019ea38d747779b84b16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Srwlock — klasa](../windows/srwlock-class.md)