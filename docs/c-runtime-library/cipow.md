---
title: _CIpow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIpow
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
dev_langs: C++
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0bed34f3107f598d2070b39ac011f786b498c519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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