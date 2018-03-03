---
title: "Kompilatora (poziom 1) ostrzeżenie C4532 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44aae61190b20bf1ef93b586c02e88837d487324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4532"></a>Kompilator C4532 ostrzegawcze (poziom 1)
"continue": skok poza __finally/bloku finally ma niezdefiniowane zachowanie podczas obsługi zakończenia  
  
 Kompilator wystąpił jeden z następujących słów kluczowych:  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 powoduje skok poza [__finally](../../cpp/try-finally-statement.md) lub [koniec](../../dotnet/finally.md) bloku podczas przerwania pracy.  
  
 Jeśli wystąpi wyjątek i gdy jest on odwinięty stosu podczas wykonywania programy obsługi zakończenia ( `__finally` lub bloki finally), i kodu w tę łódź poza `__finally` blokować przed `__finally` bloku zakończeń zachowanie jest niezdefiniowana. Formant nie może zwracać odwijaniem kod, wyjątek nie może zostać obsłużony poprawnie.  
  
 Jeśli musisz przejść z **__finally** bloków, najpierw sprawdź przerwania pracy.  
  
 Poniższy przykład generuje C4532; po prostu komentarz instrukcje skok do rozwiązania ostrzeżeń.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```