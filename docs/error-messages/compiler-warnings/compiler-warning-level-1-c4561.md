---
title: "Kompilatora (poziom 1) ostrzeżenie C4561 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4561
dev_langs: C++
helpviewer_keywords: C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3706257138c1825e4075c7b131ae272df811626
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4561"></a>Kompilator C4561 ostrzegawcze (poziom 1)
Wywołanie "__fastcall" niezgodny z "/ clr" opcja: konwertowanie na "\__stdcall"  
  
 [__Fastcall](../../cpp/fastcall.md) Konwencja wywoływania funkcji nie można używać z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora. Kompilator ignoruje wywołań `__fastcall`. Aby usunąć to ostrzeżenie, Usuń wywołania do **__fastcall** lub skompiluj bez **/CLR**.  
  
 Poniższy przykład generuje C4561:  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```