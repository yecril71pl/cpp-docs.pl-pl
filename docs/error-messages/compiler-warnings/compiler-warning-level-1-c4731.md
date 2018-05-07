---
title: Kompilatora (poziom 1) ostrzeżenie C4731 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31bdf972ef3791760469251dc4d0bf19627bded2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4731"></a>Kompilator C4731 ostrzegawcze (poziom 1)
"wskaźnik": "register" zmodyfikowany przez wbudowany kod asemblera rejestr wskaźnika ramki  
  
 Rejestr wskaźnika ramki została zmodyfikowana. Należy zapisać i przywrócić rejestr w wbudowanego zestawu bloku lub ramki zmiennej użytkownika (lokalnego lub parametru, w zależności od zmodyfikować rejestr) lub kod może nie działać prawidłowo.  
  
 Poniższy przykład generuje C4731:  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP jest wskaźnika ramki (niedopuszczalne FPO) i jest modyfikowana. Gdy `p` jest nowsza odwołać się do odwołuje się do względem `EBP`. Ale `EBP` został zastąpiony przez kod, więc program nie będzie działać prawidłowo i może nawet fault.