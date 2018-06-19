---
title: C2561 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8ece9a3d9347a5179844cbfca3425870c25e2f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230907"
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