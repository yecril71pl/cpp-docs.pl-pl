---
title: ModuleType — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 831f1fbcb2da205fa08286a1fbbbf414e66075d4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019933"
---
# <a name="moduletype-enumeration"></a>ModuleType — Wyliczenie
Określa, czy moduł powinien obsługiwać wewnątrz procesowego lub serwera spoza procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum ModuleType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InProc`|Serwer usługi w trakcie.|  
|`OutOfProc`|Serwer usługi poza procesem.|  
|`DisableCaching`|Wyłącz mechanizm buforowania w Module.|  
|`InProcDisableCaching`|Kombinacja `InProc` i `DisableCaching`.|  
|`OutOfProcDisableCaching`|Kombinacja `OutOfProc` i `DisableCaching`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)