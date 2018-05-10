---
title: no_dual_interfaces — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8923adb4cf2e92d72bf656064c6de8fc66e2a91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Określonego języka C++**  
  
 Zmienia sposób kompilator generuje funkcje otoki dla metody interfejsu podwójny.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>Uwagi  
 Normalnie otoka wywoła metodę za pośrednictwem tabeli funkcji wirtualnych dla interfejsu. Z `no_dual_interfaces`, zamiast tego wywołuje otoka **IDispatch::Invoke** można wywołać metody.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)