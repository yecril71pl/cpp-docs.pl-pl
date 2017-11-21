---
title: "Runtimeclasstype — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClassType
dev_langs: C++
helpviewer_keywords: RuntimeClassType enumeration
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 222f7d9ada76e43fa71658faa7c61e5369abd3db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)