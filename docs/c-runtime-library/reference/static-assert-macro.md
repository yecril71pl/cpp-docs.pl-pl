---
title: "_Static_assert — makro | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords: _STATIC_ASSERT
dev_langs: C++
helpviewer_keywords: _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 686ac443eb32a9ca17e77baee95b50e06c6556b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT — Makro
Oceń wyrażenia w czasie kompilacji i generuje błąd, gdy wynik jest `FALSE`.  
  
## <a name="syntax"></a>Składnia  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Wyrażenia (w tym wskaźników), którego wynikiem do różną od zera (`TRUE`) lub równa 0 (`FALSE`).  
  
## <a name="remarks"></a>Uwagi  
 Przypomina to makro [_ASSERT i _asserte — makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), ale `booleanExpression` jest oceniane w czasie kompilacji zamiast w czasie wykonywania. Jeśli `booleanExpression` daje w wyniku `FALSE` (0), [C2466 błąd kompilatora](../../error-messages/compiler-errors-1/compiler-error-c2466.md) jest generowany.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie, musimy sprawdzić czy `sizeof` `int` jest większa niż lub równa 2 bajty oraz tego, czy `sizeof` `long` jest 1 bajt. Program nie zostanie skompilowany i będzie generować [C2466 błąd kompilatora](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ponieważ `long` jest większy niż 1 bajt.  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Makra|Wymagany nagłówek|  
|-----------|---------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_ASSERT, _asserte —, _ASSERT_EXPR makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)