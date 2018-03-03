---
title: "C3642 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3dace0204f4534ee630924bd443d028efc2afc14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3642"></a>C3642 błąd kompilatora
' zwracany_typ/args': nie można wywołać funkcji w Konwencji wywołania __clrcall z natywnego kodu  
  
 Funkcja, która jest oznaczony atrybutem [__clrcall](../../cpp/clrcall.md) konwencji wywoływania nie można wywołać z kodu macierzystego (niezarządzany).  
  
 *Zwracany_typ/args* jest nazwę funkcji lub typ `__clrcall` próby wywołania funkcji.  Typ jest używany podczas nawiązywane za pomocą wskaźnika funkcji.  
  
 Wywoływanie funkcji zarządzanego z kontekstem macierzystym, można dodać funkcję "otoki", która wywoła `__clrcall` funkcji. Lub może używać mechanizmu kierowanie CLR; zobacz [porady: kierowanie funkcja wskaźników przy użyciu PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C3642:  
  
```  
// C3642.cpp  
// compile with: /clr  
using namespace System;  
struct S {  
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall  
      Console::WriteLine(s);  
   }  
   void Test2(char * s) {  
      Test(gcnew String(s));  
   }  
};  
  
#pragma unmanaged  
int main() {  
   S s;  
   s.Test("abc");   // C3642  
   s.Test2("abc");   // OK  
}  
```