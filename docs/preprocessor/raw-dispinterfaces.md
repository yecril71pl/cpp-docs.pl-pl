---
title: raw_dispinterfaces — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_dispinterfaces
dev_langs:
- C++
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 093c994de24b947c53bfc19d33213e77f3ec2593
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465238"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Określonego język C++**  
  
Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują `IDispatch::Invoke` i zwracają kod błędu HRESULT.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_dispinterfaces  
```  
  
## <a name="remarks"></a>Uwagi  
 
Jeśli ten atrybut nie jest określony, tylko ogólne są generowane otoki, która generuje wyjątków C++ w przypadku awarii.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)