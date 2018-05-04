---
title: _CIatan2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIatan2
apilocation:
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIatan2
- _CIatan2
dev_langs:
- C++
helpviewer_keywords:
- _CIatan2 intrinsic
- CIatan2 intrinsic
ms.assetid: 31f8cc78-b79f-4576-b73b-8add18e08680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33abe3dd332bdb55decde308d67d0e1af13e13f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ciatan2"></a>_CIatan2
Oblicza tangens *x* / *y* gdzie *x* i *y* wartości wierzchołku stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _CIatan2();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta wersja `atan2` funkcja ma specjalne Konwencja wywoływania obsługującą przez kompilator. Przyspiesza wykonywanie, ponieważ uniemożliwia kopie generowany, a ułatwia alokacja rejestru.  
  
 Wartość wynikową spoczywa na wierzchu stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** x86  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)