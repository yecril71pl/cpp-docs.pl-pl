---
title: "Kompilatora (poziom 1) ostrzeżenie C4461 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4461
dev_langs: C++
helpviewer_keywords: C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc417e7044eb3eac12365676c6c1be9abeddfed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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