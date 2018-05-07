---
title: Kompilatora (poziom 1) ostrzeżenie C4461 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2884daeb7497f6664cecf864ec705891cac62f48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4461"></a>Kompilator C4461 ostrzegawcze (poziom 1)
'type': Ta klasa ma finalizator "finalizator", ale nie ma destruktora "dtor"  
  
 Obecność finalizator w typie oznacza zasoby do usunięcia. Jeśli finalizator jawnie jest wywoływana z typu destruktor, środowisko uruchomieniowe języka wspólnego Określa, kiedy finalizator, została uruchomiona po obiektu wykracza poza zakres.  
  
 Jeśli zdefiniowanie destruktora w typie, a następnie jawnie wywołać finalizatora z destruktor, sposób niejednoznaczny można uruchomić Twojej finalizatora.  
  
 Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4461.  
  
```  
// C4461.cpp  
// compile with: /W1 /clr /c  
ref class A {  
protected:  
   !A() {}   // C4461  
};  
  
// OK  
ref struct B {  
   ~B() {  
      B::!B();  
   }  
  
   !B() {}  
};  
```