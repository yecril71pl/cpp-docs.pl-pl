---
title: "check_stack — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
dev_langs: C++
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6f72036e897a51b907fb41387f25fd7d20df69e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="checkstack"></a>check_stack
Instruuje kompilator, aby wyłączyć sondy stosu **poza** (lub  **-** ) jest określona, lub Włącz sondy stosu, jeśli **na** (lub  **+** ) został określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | -}  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie zostanie podany argument nie, sondy stosu są traktowane zgodnie z domyślnym. Tej pragmy zaczyna obowiązywać przy pierwszej funkcji zdefiniowane po pragma jest widoczna. Sondy stosu należą ani do makr ani funkcje, które są wbudowane wygenerowanego.  
  
 Jeśli nie zostanie nadana argument **check_stack —** pragma, sprawdzanie stosu wraca do zachowania określona w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [kompilatora](../build/reference/compiler-options.md). Interakcja z **check_stack — #pragma** i [/GS](../build/reference/gs-control-stack-checking-calls.md) opcji znajduje się w poniższej tabeli.  
  
### <a name="using-the-checkstack-pragma"></a>Przy użyciu check_stack — wartość dyrektywy Pragma  
  
|Składnia|Skompilowane z<br /><br /> Opcja/GS?|Akcja|  
|------------|------------------------------------|------------|  
|**(#pragma check_stack —)** lub<br /><br /> **check_stack — #pragma**|Tak|Wyłącza funkcje, które należy wykonać sprawdzanie stosu|  
|**(#pragma check_stack —)** lub<br /><br /> **check_stack — #pragma**|Nie|Włącza sprawdzanie stosu dla funkcji, które należy wykonać|  
|**#pragma check_stack(on)**<br /><br /> lub **check_stack — #pragma +**|Tak lub nie|Włącza sprawdzanie stosu dla funkcji, które należy wykonać|  
|**#pragma check_stack(off)**<br /><br /> lub **check_stack — #pragma -**|Tak lub nie|Wyłącza funkcje, które należy wykonać sprawdzanie stosu|  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)