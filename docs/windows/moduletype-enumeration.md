---
title: "ModuleType — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ModuleType
dev_langs: C++
helpviewer_keywords: ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a516795124ec3de6bb90102b3ea200d3365f33c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)