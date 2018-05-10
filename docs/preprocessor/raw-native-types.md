---
title: raw_native_types — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_native_types
dev_langs:
- C++
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5baa3204b14da53f6a6a3232874e0ac7de0fd91b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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