---
title: Inspectableclass — makro | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 922f7f74771125aed0122c408ef902da2569e5c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873774"
---
# <a name="inspectableclass-macro"></a>InspectableClass — Makro
Ustawia poziom nazwy i zaufania klasy środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtimeClassName`  
 Pełne tekstową Nazwa klasy środowiska wykonawczego.  
  
 `trustLevel`  
 Jeden z [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) wyliczyć wartości.  
  
## <a name="remarks"></a>Uwagi  
 `InspectableClass` Makro może być używany tylko z typów środowiska wykonawczego systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [RuntimeClass, klasa](../windows/runtimeclass-class.md)