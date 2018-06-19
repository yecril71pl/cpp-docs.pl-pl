---
title: Kompilatora (poziom 1) ostrzeżenie C4532 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4532
dev_langs:
- C++
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e37d36f565cc63c7cef9954a78e14ed60d676996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285863"
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