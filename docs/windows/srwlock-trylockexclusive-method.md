---
title: SRWLock::TryLockExclusive, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 674a7dced019926e6ea07b41641eb42db70c45a0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013483"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive — Metoda
Próbuje pobrać **SRWLock** obiektu w trybie wyłączności dla bieżącej lub określonej **SRWLock** obiektu. Jeśli wywołanie zakończy się pomyślnie, wątek wywołujący przejmuje na własność blokadę.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *lock*  
 Wskaźnik do **SRWLock** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia **SRWLock** obiektu w trybie wyłączności i Wątek wywołujący przejmuje na własność blokadę. W przeciwnym razie **SRWLock** obiektu, którego stan jest nieprawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [SRWLock, klasa](../windows/srwlock-class.md)