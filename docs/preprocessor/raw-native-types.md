---
title: "raw_native_types — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4908f1f06ef0479121d3ec5ac8fa56a797ed05ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="rawnativetypes"></a>raw_native_types
**Określonego języka C++**  
  
 Wyłącza używanie klas obsługi COM w funkcjach otoki wysokiego poziomu, a zamiast tego wymusza stosowanie typów danych niskiego poziomu.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie wysokiego poziomu metody obsługi błędów używać klas obsługi COM [_bstr_t](../cpp/bstr-t-class.md) i [_variant_t](../cpp/variant-t-class.md) zamiast `BSTR` i **VARIANT** typy danych i wskaźniki interfejsu COM RAW. Te klasy Hermetyzowanie szczegóły alokowanie i dealokowanie pamięci magazynu dla tych typów danych i znacznie upraszcza operacji rzutowania i konwersji typu.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)