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
ms.openlocfilehash: d36355c9f64f9f5c827ef8c4d5b3cb6a77d17b65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876839"
---
# <a name="moduletype-enumeration"></a>ModuleType — Wyliczenie
Określa, czy moduł powinien obsługiwać server wewnątrzprocesowe lub serwer poza procesem.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum ModuleType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InProc`|W procesie serwera.|  
|`OutOfProc`|Serwer poza procesem.|  
|`DisableCaching`|Wyłącz mechanizm buforowania dla modułu.|  
|`InProcDisableCaching`|Kombinacja `InProc` i `DisableCaching`.|  
|`OutOfProcDisableCaching`|Kombinacja `OutOfProc` i `DisableCaching`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)