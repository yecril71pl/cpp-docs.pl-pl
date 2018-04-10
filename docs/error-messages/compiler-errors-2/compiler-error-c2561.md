---
title: C2561 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 604c5b4ce8c8e1b5477d076a061fdf56fdfd9c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2561"></a>C2561 błąd kompilatora
"identyfikator": funkcja musi zwracać wartość  
  
 Funkcja została zadeklarowana jako zwracanie wartości, ale nie zawiera definicji funkcji `return` instrukcji.  
  
 Przyczyną tego błędu może być prototypu Niepoprawna funkcja:  
  
1.  Jeśli funkcja nie zwraca wartości, należy zadeklarować funkcji z typem zwracanym [void](../../cpp/void-cpp.md).  
  
2.  Sprawdź, czy wszystkie możliwe gałęzie funkcji zwracać wartość typ zadeklarowany w prototypu.  
  
3.  Funkcje języka C++ zawierający wbudowanego zestawu procedury, których są przechowywane wartości zwracanej w `AX` rejestru może być konieczne instrukcji return. Skopiuj wartość `AX` do tymczasowej zmiennej i powrót z funkcji tej zmiennej.  
  
 Poniższy przykład generuje C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```