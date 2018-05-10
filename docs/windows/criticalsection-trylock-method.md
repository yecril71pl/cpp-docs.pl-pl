---
title: CriticalSection::TryLock — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4ee99d82212d0d6cdd610b4565bd9292a0265dc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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