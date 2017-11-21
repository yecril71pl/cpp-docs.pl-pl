---
title: "Kompilatora (poziom 1) ostrzeżenie C4722 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4722
dev_langs: C++
helpviewer_keywords: C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8616fe9834b0f73445bbcb8ffea4d35af3895b12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4722"></a>Kompilator C4722 ostrzegawcze (poziom 1)
"Funkcja": destruktor nigdy nie powraca, potencjalny wyciek pamięci  
  
 Przepływ sterowania kończy w destruktora. Wątek lub cały program zostanie zamknięty i nie można zwolnić przydzielone zasoby.  Ponadto jeśli destruktora zostanie wywołana dla odwijanie stosu podczas przetwarzania wyjątek, zachowanie pliku wykonywalnego jest niezdefiniowany.  
  
 Aby rozwiązać, Usuń powodujący destruktor nie zwracał wywołania funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4722:  
  
```  
// C4722.cpp  
// compile with: /O1 /W1 /c  
#include <stdlib.h>  
class C {  
public:  
   C();  
   ~C() { exit(1); };   // C4722  
};  
  
extern void func (C*);  
  
void Test(){  
   C x;  
   func(&x);  
   // control will not leave Test because destructor will exit  
}  
```