---
title: Factorycacheflags — wyliczenie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5ba3d9b75ff72399e1b9a027c937c24bba4a6c37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874333"
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
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)