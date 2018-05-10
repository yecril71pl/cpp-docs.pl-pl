---
title: raw_interfaces_only — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4643181bf70bc92f4ef5e88b8a9add1ba7bdaad7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)