---
title: "ChainInterfaces::Verify — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs: C++
helpviewer_keywords: Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f6cd836d946265f26925e6bc7a9ef8191df93b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify — Metoda
Sprawdza, czy każdy interfejs zdefiniowane przez parametry szablonu `I0` za pośrednictwem `I9` dziedziczy IUnknown i/lub IInspectable oraz że `I0` dziedziczy `I1` za pośrednictwem `I9`.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Uwagi  
 W przypadku niepowodzenia operacji sprawdzania `static_assert` emituje komunikat o błędzie opisujący błąd.  
  
## <a name="remarks"></a>Uwagi  
 Parametry szablonu `I0` i `I1` są wymagane, parametry i `I2` za pośrednictwem `I9` są opcjonalne.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Chaininterfaces — struktura](../windows/chaininterfaces-structure.md)