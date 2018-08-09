---
title: Asyncresulttype — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7989f28ae9c9e3af4c73ec454487d34dd7cff570
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644758"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType — Wyliczenie
Określa typ wyniku zwracanego przez `GetResults()` metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum AsyncResultType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`MultipleResults`|Zbiór wielu wyników, które są prezentowane stopniowo między `Start` stanu i przed `Close()` jest wywoływana.|  
|`SingleResult`|Pojedynczy wynik, który jest przedstawiony po `Complete` wystąpi zdarzenie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)