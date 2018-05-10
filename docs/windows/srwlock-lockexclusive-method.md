---
title: SRWLock::LockExclusive — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36ae694365b58cb10666e5d8af67269b2c4f125c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive — Metoda
Uzyskuje obiekt srwlock — w trybie wyłączności.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLockExclusive LockExclusive();  
  
static SyncLockExclusive LockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lock`  
 Wskaźnik do obiektu srwlock —.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt srwlock — w trybie wyłączności.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [SRWLock, klasa](../windows/srwlock-class.md)