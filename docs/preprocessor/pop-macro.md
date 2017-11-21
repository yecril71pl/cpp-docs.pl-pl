---
title: pop_macro | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
dev_langs: C++
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec14a1ca37c62d2f076315279ae6267adda3b958
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="popmacro"></a>pop_macro
Ustawia wartość *macro_name* makro wartość górnej części stosu dla tego makra.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma pop_macro("  
macro_name  
")  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Najpierw należy wygenerować [dyrektywy push_macro](../preprocessor/push-macro.md) dla *macro_name* wcześniej **pop_macro**.  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directives_pop_macro.cpp  
// compile with: /W1  
#include <stdio.h>  
#define X 1  
#define Y 2  
  
int main() {  
   printf("%d",X);  
   printf("\n%d",Y);  
   #define Y 3   // C4005  
   #pragma push_macro("Y")  
   #pragma push_macro("X")  
   printf("\n%d",X);  
   #define X 2   // C4005  
   printf("\n%d",X);  
   #pragma pop_macro("X")  
   printf("\n%d",X);  
   #pragma pop_macro("Y")  
   printf("\n%d",Y);  
}  
```  
  
```Output  
1  
2  
1  
2  
1  
3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)