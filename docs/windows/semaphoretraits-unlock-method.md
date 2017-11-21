---
title: "SemaphoreTraits::Unlock — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs: C++
helpviewer_keywords: Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9431dea4d09f320727f6ae35b4c296cbb9799863
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock — Metoda
Kontrola wersji zasobu udostępnionego.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Dojście do obiektu semafora.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli operacja unlock zakończy się niepowodzeniem, Unlock() emituje komunikat o błędzie wskazujący przyczynę niepowodzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Zobacz też  
 [Semaphoretraits — struktura](../windows/semaphoretraits-structure.md)