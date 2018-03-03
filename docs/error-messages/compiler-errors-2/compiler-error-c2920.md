---
title: "C2920 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2920
dev_langs:
- C++
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba5a7706dc4607897cb2ef71f2072209e0516f53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2920"></a>C2920 błąd kompilatora
Ponowna definicja: "class": szablon klasy lub ogólny został już zadeklarowany jako "type"  
  
 Klasy ogólne lub szablon ma wiele deklaracje, które nie są równoważne. Aby naprawić ten błąd, użyj różnych nazw dla różnych typów, lub usuń ponowna definicja nazwy typu.  
  
 Poniższy przykład generuje C2920 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2920.cpp  
// compile with: /c  
typedef int TC1;  
template <class T>   
struct TC1 {};   // C2920  
struct TC2 {};   // OK - fix by using a different name  
```  
  
 C2920 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2920b.cpp  
// compile with: /clr /c  
typedef int GC1;  
generic <class T>   
ref struct GC1 {};   // C2920  
ref struct GC2 {};   // OK - fix by using a different name  
```