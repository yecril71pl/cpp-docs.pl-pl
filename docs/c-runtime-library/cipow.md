---
title: _CIpow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIpow
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIpow
- _CIpow
dev_langs:
- C++
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c3500c0bd17b2638026f45c23b047e2bee411cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cipow"></a>_CIpow
Oblicza *x* do *y* zasilania na podstawie górnej wartości na stosie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _CIpow();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja `pow` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany, a ułatwia alokacja rejestru.  
  
 Wartość wynikową spoczywa na wierzchu stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** x86  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)