---
title: _CIlog10 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CIlog10
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIlog10
- _CIlog10
dev_langs: C++
helpviewer_keywords:
- _CIlog10 intrinsic
- CIlog10 intrinsic
ms.assetid: 05d7fcaa-3cff-4cc5-8d44-015e7cacba24
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8eb203750491475b7e615d5f7d3ff940a772f6a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cilog10"></a>_CIlog10
Wykonuje `log10` operacja na wartości top w stosie.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _CIlog10();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja `log10` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Funkcja przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowane i pomaga w alokacja rejestru.  
  
 Wartość wynikową spoczywa na wierzchu stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** x86  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [logf —, log10, log10f — w Dzienniku](../c-runtime-library/reference/log-logf-log10-log10f.md)