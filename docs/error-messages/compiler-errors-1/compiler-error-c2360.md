---
title: C2360 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2360
dev_langs:
- C++
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c24a44222a01d66c57aab340c5a06469f212e285
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2360"></a>C2360 błąd kompilatora
Inicjalizacja "identyfikatora" jest pomijana przy etykiecie "case"  
  
 Inicjowanie `identifier` był pomijany w `switch` instrukcji. Nie można przeskoczyć poza deklaracji z inicjatora, chyba że deklaracja jest ujęta w bloku. (Chyba że jest on zadeklarowany w bloku, zmienna znajduje się w zakresie do końca `switch` instrukcji.)  
  
 Poniższy przykład generuje C2360:  
  
```  
// C2360.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      int i = 1;  
      { int j = 1; }  
   case 1 :   // C2360  
      int k = 1;  
   }  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2360b.cpp  
int main() {  
   int x = 0;  
   switch ( x ) {  
   case 0 :  
      { int j = 1; int i = 1;}  
   case 1 :  
      int k = 1;  
   }  
}  
```