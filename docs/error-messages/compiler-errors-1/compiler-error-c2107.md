---
title: C2107 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2107
dev_langs:
- C++
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a4d173162d290644f450614e19aaa96615c0ae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171669"
---
# <a name="compiler-error-c2107"></a>C2107 błąd kompilatora
Nieprawidłowy indeks, pośrednik niedozwolony  
  
 Indeks dolny jest stosowany do wyrażenie, które nie zostało oszacowane jako wskaźnik.  
  
## <a name="example"></a>Przykład  
 C2107 może wystąpić, jeśli używasz niepoprawnie `this` wskaźnika indeksatora domyślny typ dostępu do typu wartości. Aby uzyskać więcej informacji, zobacz [semantyka wskaźnika](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).  
  
 Poniższy przykład generuje C2107.  
  
```  
// C2107.cpp  
// compile with: /clr  
using namespace System;  
  
value struct B {  
   property String ^ default[String ^] {  
      String ^ get(String ^ data) {  
         return "abc";  
      }  
   }  
   void Test() {  
      Console::WriteLine("{0}", this["aa"]);   // C2107  
      Console::WriteLine("{0}", this->default["aa"]);   // OK  
   }  
};  
  
int main() {  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```