---
title: "Factorycacheflags — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::FactoryCacheFlags
dev_langs: C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb4efeb716255ae67a01fca7cf04a54816e227d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie
Określa, czy obiekty są buforowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie fabryki zasad buforowania jest określony jako [ModuleType](../windows/moduletype-enumeration.md) parametr szablonu podczas tworzenia [modułu](../windows/module-class.md) obiektu. Aby zastąpić te zasady, określić `FactoryCacheFlags` wartości podczas tworzenia obiektu fabryki.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|Zasady buforowania `Module` obiekt jest używany.|  
|`FactoryCacheEnabled`|Włącza buforowanie fabryki niezależnie od tego `ModuleType` parametr szablonu, który służy do tworzenia `Module` obiektu.|  
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki niezależnie od tego `ModuleType` parametr szablonu, który służy do tworzenia `Module` obiektu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)