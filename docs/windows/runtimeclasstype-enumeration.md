---
title: "Runtimeclasstype — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26016e8c95807af76484504c491ca1e6e08f8f96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType — Wyliczenie
Określa typ [runtimeclass —](../windows/runtimeclass-class.md) wystąpienia, która jest obsługiwana.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ClassicCom`|Klasa klasycznego środowiska uruchomieniowego COM.|  
|`Delegate`|Odpowiednikiem **ClassicCom**.|  
|`InhibitFtmBase`|Wyłącza `FtmBase` pomocy technicznej podczas `__WRL_CONFIGURATION_LEGACY__` nie jest zdefiniowany.|  
|`InhibitWeakReference`|Wyłącza obsługę słabe odwołanie.|  
|`WinRt`|Klasa środowiska uruchomieniowego systemu Windows.|  
|`WinRtClassicComMix`|Kombinację `WinRt` i `ClassicCom`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)