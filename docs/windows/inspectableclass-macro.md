---
title: "Inspectableclass — makro | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::InspectableClass
dev_langs: C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f9cb2ac0ef10492d226fee9ef40d95c18b4f3ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Runtimeclass — klasa](../windows/runtimeclass-class.md)