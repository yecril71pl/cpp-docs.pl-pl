---
title: "Kompilatora (poziom 1) ostrzeżenie C4731 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4731
dev_langs: C++
helpviewer_keywords: C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d8c59a22166c3f4f44db3bea43e241a2199009d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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