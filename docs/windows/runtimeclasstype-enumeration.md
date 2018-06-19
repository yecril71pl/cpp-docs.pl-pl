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
ms.openlocfilehash: 43ab0a738af4c6bc92d42c0884827b574946d2ea
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892406"
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