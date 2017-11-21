---
title: "Kompilatora (poziom 3) ostrzeżenie C4823 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4823
dev_langs: C++
helpviewer_keywords: C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af4b7e220957722793458a283244092574d05fa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4823"></a>Kompilator C4823 ostrzegawcze (poziom 3)
"Funkcja": używa wskaźników przypinanych ale unwind semantyki nie są włączone. Należy rozważyć użycie opcji/eha  
  
Odpiąć obiektu na stercie zarządzanej wskazywana przez wskaźnik przypinania zadeklarowany w zakresie bloku, kompilator symuluje zachowanie destruktory klas lokalnych "imitujących" przypiętego wskaźnika ma destruktor, który nullifies wskaźnika. Aby włączyć wywołanie destruktora po zgłoszeniu wyjątku, należy włączyć rozwinięcia obiektu, co można zrobić za pomocą [/ehsc](../../build/reference/eh-exception-handling-model.md).  
  
Można też ręcznie odpiąć obiektu i zignorować to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C4823.  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  
