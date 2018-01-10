---
title: "Kompilatora (poziom 4) ostrzeżenie C4481 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4481
dev_langs: C++
helpviewer_keywords: C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52c296251e22adef2702aa9feba2b1fe2bc5122e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4481"></a>Kompilator C4481 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: specyfikator "— słowo kluczowe" override  
  
 Słowo kluczowe użyto nie znajduje się w standard C++, na przykład jeden specyfikatorów zastąpienia, które działa także w/CLR.  Aby uzyskać więcej informacji, zobacz,  
  
-   [/ CLR (kompilacja języka wspólnego środowiska wykonawczego)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Specyfikatory zastąpienia](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4481.  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```