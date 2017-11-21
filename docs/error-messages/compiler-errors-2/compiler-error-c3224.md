---
title: "C3224 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3224
dev_langs: C++
helpviewer_keywords: C3224
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 383d7a5d4eb77efeaaabbbd2e29c3618f9a7b582
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3224"></a>C3224 błąd kompilatora
'type': Brak przeciążonej klasy generycznej nie przyjmuje argumentów typu ogólnego "number"  
  
 Kompilator nie można odnaleźć odpowiedniego przeciążenia.  
  
 Poniższy przykład generuje C3224:  
  
```  
// C3224.cs  
// compile with: /target:library  
public class C<T> {}  
public class C<T,U> {}  
```  
  
 a następnie  
  
```  
// C3224b.cpp  
// compile with: /clr  
#using "C3224.dll"  
int main() {  
   C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224  
   C<int,int>^ c2 = gcnew C<int,int>();   // OK  
}  
```