---
title: CriticalSection::Lock — Metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c873494a702802b8ead3dab9cac28557664f618
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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