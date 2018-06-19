---
title: SemaphoreTraits::Unlock — Metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0914c6ff83e881f92963fc8a548ddeff587db75e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892250"
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
 [SemaphoreTraits, struktura](../windows/semaphoretraits-structure.md)