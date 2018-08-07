---
title: Runtimeclasstype — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassType
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4464d236a85e06bf907f738657a4a0707e14a5e1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603504"
---
# <a name="runtimeclasstype-enumeration"></a>RuntimeClassType — Wyliczenie
Określa typ [RuntimeClass](../windows/runtimeclass-class.md) wystąpienia, która jest obsługiwana.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum RuntimeClassType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ClassicCom`|Klasa klasycznego środowiska uruchomieniowego COM.|  
|`Delegate`|Odpowiednikiem `ClassicCom`.|  
|`InhibitFtmBase`|Wyłącza `FtmBase` obsługi podczas `__WRL_CONFIGURATION_LEGACY__` nie został zdefiniowany.|  
|`InhibitWeakReference`|Wyłącza obsługę słabe odwołanie.|  
|`WinRt`|Klasa środowiska wykonawczego Windows.|  
|`WinRtClassicComMix`|Kombinacji `WinRt` i `ClassicCom`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)