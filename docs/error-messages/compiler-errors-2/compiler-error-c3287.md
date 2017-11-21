---
title: "C3287 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3287
dev_langs: C++
helpviewer_keywords: C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b09d2af16ca6d38e476e7298b2b5fb61b2b30129
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3287"></a>C3287 błąd kompilatora
Typ "type" (typ zwrotny z GetEnumerator) musi mieć odpowiednie publicznego funkcję członkowską MoveNext oraz publiczną właściwość Current  
  
 Klasy kolekcji zdefiniowane przez użytkownika musi zawierać definicje `MoveNext` i `Current`.  
  
 Zobacz [porady: kolekcja Iterate Over a User-Defined o dla każdego](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3287.  
  
```  
// C3287.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {  
   bool MoveNext() {  
      return true;  
   }  
   property Object^ Current {  
      Object^ get() {  
         Object ^ o = gcnew Object;  
         return o;  
      }  
   }  
};  
  
ref struct R2 {  
   R ^GetEnumerator() {  
      R^ r = gcnew R;  
      return r;  
   }  
};  
  
ref struct T {};  
  
ref struct T2 {  
   T ^GetEnumerator() {  
      T^ t = gcnew T;  
      return t;  
   }  
};  
  
int main() {  
   for each (int i in gcnew T2) {}   // C3287  
   for each (int i in gcnew R2) {}   // OK  
}  
```