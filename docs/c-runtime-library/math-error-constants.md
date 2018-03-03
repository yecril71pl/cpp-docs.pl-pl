---
title: "Stałe błędów matematycznych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs:
- C++
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76313854bc9bb7c9a624836c47d0178978f8befd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-constants"></a>Stałe błędów matematycznych
## <a name="syntax"></a>Składnia  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Procedury matematyczne biblioteki wykonawczej mogą generować stałe błędów matematycznych.  
  
 Te błędy, opisane w następujący sposób odpowiadają typów wyjątków zdefiniowane w MATEMATYCZNYCH. H i są zwracane przez `_matherr` działać, jeśli wystąpi błąd matematyczny.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_DOMAIN`|Argument funkcji jest poza domeną funkcji.|  
|`_OVERFLOW`|Wynik jest za duży, aby mogły być reprezentowane w zwracanego typu funkcji.|  
|`_PLOSS`|Wystąpił częściowo utraciła istotności.|  
|`_SING`|Argument singularity: argument funkcji ma nieprawidłową wartość. (Na przykład wartość 0 jest przekazywany do funkcji, która wymaga wartości niezerowych.)|  
|`_TLOSS`|Wystąpił całkowitej utraty istotności.|  
|`_UNDERFLOW`|Wynik jest za mały, aby mogła być przedstawiana.|  
  
## <a name="see-also"></a>Zobacz też  
 [_matherr —](../c-runtime-library/reference/matherr.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)