---
title: "raw_dispinterfaces — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9c20cc7cab6c85f203bc83523229f50749332f3d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Określonego języka C++**  
  
 Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują **IDispatch::Invoke** i zwracać `HRESULT` kod błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten atrybut nie jest określona, tylko wysokiego poziomu otoki są generowane, które zgłaszają wyjątki C++ w razie awarii.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)