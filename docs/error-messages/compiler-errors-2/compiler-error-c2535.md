---
title: "C2535 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2535
dev_langs: C++
helpviewer_keywords: C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0af3ce8f0f3fe89d8e2f120f1b9b16383f11ef6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2535"></a>C2535 błąd kompilatora
"identyfikator": funkcja członkowska już zdefiniowana lub zadeklarowana  
  
 Ten błąd może być spowodowana przy użyciu tej samej listy parametrów formalnych w więcej niż jednej definicji lub deklaracji przeciążonej funkcji.  
  
 Jeśli z powodu funkcji Dispose C2535, zobacz [destruktory i finalizatory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Aby uzyskać więcej informacji.  
  
 Gdy kompilowany jest Projekt ATL, zobacz artykuł bazy wiedzy Knowledge Base Q241852.  
  
 Poniższy przykład generuje C2535:  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```