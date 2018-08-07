---
title: FactoryCacheFlags, wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4bd998368fb325878a81ee4954a2ceec9432fe
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570106"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags — Wyliczenie
Określa, czy obiekty są buforowane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie fabryki zasady buforowania jest określony jako [ModuleType](../windows/moduletype-enumeration.md) parametru szablonu podczas tworzenia [modułu](../windows/module-class.md) obiektu. Aby zastąpić te zasady, należy określić **FactoryCacheFlags** wartości podczas tworzenia obiektu fabryki.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|Zasady buforowania `Module` obiekt jest używany.|  
|`FactoryCacheEnabled`|Włącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|  
|`FactoryCacheDisabled`|Wyłącza buforowanie fabryki, niezależnie od wartości `ModuleType` parametr szablonu, który jest używany do tworzenia `Module` obiektu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)