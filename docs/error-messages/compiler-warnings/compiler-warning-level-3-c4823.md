---
title: Kompilatora (poziom 3) ostrzeżenie C4823 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29499a82601dcf653ff2f003441935f1d6841a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
