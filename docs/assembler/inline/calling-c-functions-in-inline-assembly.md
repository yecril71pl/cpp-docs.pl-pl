---
title: "Funkcje wywoływania C w asemblerze wbudowanym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cd162026792bf8458c3725011b583d1eeb00772
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C w asemblerze wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `__asm` Bloku można wywołać funkcji C, w tym procedury biblioteki C. Następujące przykładowe wywołania `printf` procedury biblioteki:  
  
```  
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp  
// processor: x86  
#include <stdio.h>  
  
char format[] = "%s %s\n";  
char hello[] = "Hello";  
char world[] = "world";  
int main( void )  
{  
   __asm  
   {  
      mov  eax, offset world  
      push eax  
      mov  eax, offset hello  
      push eax  
      mov  eax, offset format  
      push eax  
      call printf  
      //clean up the stack so that main can exit cleanly  
      //use the unused register ebx to do the cleanup  
      pop  ebx  
      pop  ebx  
      pop  ebx  
   }  
}  
```  
  
 Ponieważ argumenty funkcji są przekazywane na stosie, po prostu push wymagane argumenty — ciąg wskaźniki w poprzednim przykładzie — przed wywołaniem funkcji. Argumenty są usuwane w odwrotnej kolejności, więc pochodzą ze stosu w odpowiedni sposób. Aby emulować instrukcji C  
  
```  
printf( format, hello, world );  
```  
  
 wskaźniki do wypchnięcia przykładzie `world`, `hello`, i `format`, w tej kolejności, a następnie wywołania `printf`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Asembler wbudowany](../../assembler/inline/inline-assembler.md)