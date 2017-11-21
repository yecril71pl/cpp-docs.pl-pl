---
title: "Kompilatora (poziom 3) ostrzeżenie C4197 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4197
dev_langs: C++
helpviewer_keywords: C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08ad91be08a3690e6505a252eb6559d274e2f3ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4197"></a>Kompilator C4197 ostrzegawcze (poziom 3)
'type': rzutowaniu volatile najwyższego poziomu jest ignorowane.  
  
 Kompilator wykryto Rzutowanie na typ r, który jest kwalifikowany za pomocą [volatile](../../cpp/volatile-cpp.md), lub rzutowanie typu r niektórych typ, który jest kwalifikowany za pomocą nietrwałych. Zgodnie z C standard (ppkt 6.5.3) właściwości skojarzone z kwalifikowaną typy są przydatne tylko w przypadku wyrażenia wartości l.  
  
 Poniższy przykład generuje C4197:  
  
```  
// C4197.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <signal.h>  
#include <stdlib.h>  
  
void sigproc(int);  
struct S  
{  
   int i;  
} s;  
  
int main()  
{  
   signal(SIGINT, sigproc);  
   s.i = 1;  
   S *pS = &s;  
   for ( ; (volatile int)pS->i ; )   // C4197  
      break;  
   // for ( ; *(volatile int *)&pS->i ; )   // OK  
   //    break;  
}  
  
void sigproc(int) // ctrl-C  
{  
   signal(SIGINT, sigproc);  
   s.i = 0;  
}  
  
```