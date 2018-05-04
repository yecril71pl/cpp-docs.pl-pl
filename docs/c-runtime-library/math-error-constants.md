---
title: Stałe błędów matematycznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb491e8073acf2af525814b595ce79365df0fa1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [_matherr](../c-runtime-library/reference/matherr.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)