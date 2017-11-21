---
title: "Kompilatora (poziom 1) ostrzeżenie C4733 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4733
dev_langs: C++
helpviewer_keywords: C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0fc99bf8c0d3397a11b6e0b06c582a81dd2b4875
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4733"></a>Kompilator C4733 ostrzegawcze (poziom 1)
Wbudowanego asm przypisanie do "FS:0": obsługa nie jest zarejestrowana jako bezpieczna Obsługa  
  
 Funkcję przy użyciu wartości w FS:0, aby dodać nowy program obsługi wyjątku może nie działać z bezpiecznym wyjątkami, ponieważ program obsługi nie jest zarejestrowany jako prawidłowego programu obsługi wyjątków (zobacz [opcja/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).  
  
 Aby usunąć to ostrzeżenie, albo usuń definicję FS:0 lub wyłącz to ostrzeżenie i użyj [. SAFESEH](../../assembler/masm/dot-safeseh.md) do określenia bezpieczną obsługę wyjątków.  
  
 Poniższy przykład generuje C4733:  
  
```  
// C4733.cpp  
// compile with: /W1 /c  
// processor: x86  
#include "stdlib.h"  
#include "stdio.h"  
void my_handler()  
{  
   printf("Hello from my_handler\n");  
   exit(1);  
}  
  
int main()  
{  
   _asm {  
      push    my_handler  
      mov     eax, DWORD PTR fs:0  
      push    eax  
      mov     DWORD PTR fs:0, esp   // C4733  
   }  
  
   *(int*)0 = 0;  
}  
```