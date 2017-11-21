---
title: "Kompilatora (poziom 4) ostrzeżenie C4339 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4339
dev_langs: C++
helpviewer_keywords: C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 48906dbea56c3408384a31e9855a8ac31abd5f37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4339"></a>Kompilator C4339 ostrzegawcze (poziom 4)
"type": użycie niezdefiniowanego typu wykryte w WinRT lub CLR meta-data - użycie tego typu może spowodować wyjątek czasu wykonywania  
  
 Typ nie został zdefiniowany w kodzie, który został skompilowany dla środowiska wykonawczego systemu Windows lub środowisko uruchomieniowe języka wspólnego. Definiowanie typu w celu uniknięcia wyjątek czasu wykonywania to możliwe.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4339 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```