---
title: "raw_interfaces_only — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eff60ded57ae66b43dee4b3b95699ad498fa0358
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Określonego języka C++**  
  
 Pomija generację funkcje otoki Obsługa błędów i [właściwości](../cpp/property-cpp.md) deklaracje korzystających z tych funkcji otoki.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>Uwagi  
 `raw_interfaces_only` Atrybut powoduje również domyślny prefiks używać w nazwach funkcji niż właściwość do usunięcia. Zazwyczaj jest prefiks **raw_**. Jeśli ten atrybut jest określony, nazwy funkcji są bezpośrednio z biblioteki typów.  
  
 Ten atrybut umożliwia uwidocznienie niskiego poziomu zawartość biblioteki typów.  
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)