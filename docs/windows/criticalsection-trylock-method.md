---
title: "CriticalSection::TryLock — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2bd717e3a91d2e0210adced36e33a89f3752fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock — Metoda
Próbuje wpisz sekcja krytyczna bez blokowania. Jeśli połączenie zostanie nawiązane, wątek wywołujący przejmuje sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cs`  
 Obiekt określony przez użytkownika sekcja krytyczna.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość niezerową, jeśli pomyślnie wprowadzono sekcja krytyczna lub bieżący wątek już jest właścicielem sekcja krytyczna. Zero, jeśli inny wątek już właścicielem sekcja krytyczna.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy **TryLock** funkcji ma wpływ na bieżący obiekt sekcja krytyczna. Drugi **TryLock** funkcji ma wpływ na określone przez użytkownika sekcja krytyczna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSection, klasa](../windows/criticalsection-class.md)