---
title: "CriticalSection::Lock — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af996faeebd0fcddb85993badd71ceecd32d494e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock — Metoda
Czeka na prawo własności obiektu określona sekcja krytyczna. Funkcja zwraca, gdy wątek wywołujący jest własność.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cs`  
 Obiekt określony przez użytkownika sekcja krytyczna.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt blokady, który może służyć do odblokowania bieżącej sekcji krytycznych.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy **blokady** funkcji ma wpływ na bieżący obiekt sekcja krytyczna. Drugi **blokady** funkcji ma wpływ na określone przez użytkownika sekcja krytyczna.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [CriticalSection, klasa](../windows/criticalsection-class.md)