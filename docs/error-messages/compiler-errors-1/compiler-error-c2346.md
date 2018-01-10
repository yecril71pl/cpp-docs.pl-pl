---
title: "C2346 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2346
dev_langs: C++
helpviewer_keywords: C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 769d5addc47ead8ffb338d5fbef313cd46735d31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2346"></a>C2346 błąd kompilatora
"Funkcja" nie można skompilować jako natywny: Przyczyna  
  
 Kompilator nie może skompilować funkcję do MSIL.  
  
 Aby uzyskać więcej informacji, zobacz [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Usuń kod w funkcji nie może zostać skompilowane do MSIL.  
  
2.  Albo nie Kompiluj moduł **/CLR**, lub Oznacz funkcji jako niezarządzane z pragma niezarządzane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2346.  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```