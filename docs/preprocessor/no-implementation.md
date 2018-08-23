---
title: no_implementation — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbf715e2cbd19d139904438e722e4d0b72e29f29
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464454"
---
# <a name="noimplementation"></a>no_implementation
**Określonego język C++**  
  
Powoduje pominięcie generowania nagłówka .tli, który zawiera implementacje funkcji elementów członkowskich otoki.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Uwagi  
 
Jeśli ten atrybut jest określony, nagłówku .tlh, za pomocą deklaracji do udostępnienia biblioteki typów elementów, zostanie wygenerowany bez `#include` instrukcję, aby uwzględnić plik nagłówka .tli.  
  
Ten atrybut jest używany w połączeniu z [implementation_only —](../preprocessor/implementation-only.md).  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)