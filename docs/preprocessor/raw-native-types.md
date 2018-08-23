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
ms.openlocfilehash: b09e36e793608167a4ce64a9124d7dafbaf9ec62
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466331"
---
# <a name="rawnativetypes"></a>raw_native_types
**Określonego język C++**  
  
Wyłącza używanie klas obsługi COM w funkcjach otoki wysokiego poziomu, a zamiast tego wymusza stosowanie typów danych niskiego poziomu.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_native_types  
```  
  
## <a name="remarks"></a>Uwagi  
 
Domyślnie wysokiego poziomu metody obsługi błędów za pomocą klas obsługi COM [_bstr_t](../cpp/bstr-t-class.md) i [_variant_t](../cpp/variant-t-class.md) zamiast `BSTR` i `VARIANT` i typy danych COM surowego interfejsu wskaźników. W ramach tych zajęć hermetyzacji szczegółów alokowanie i dealokowanie pamięci magazynu dla tych typów danych i znacznie upraszczają operacji rzutowania i konwersji typu.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)