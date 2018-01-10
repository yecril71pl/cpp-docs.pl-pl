---
title: "C2381 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2381
dev_langs: C++
helpviewer_keywords: C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5871a20eb09b11d47200575033f3a67b98864369
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2381"></a>C2381 błąd kompilatora
"Funkcja": zmiana definicji; różni się __declspec(noreturn)  
  
 Funkcja została zadeklarowana i następnie zdefiniowane, ale z definicją używaną [noreturn](../../cpp/noreturn.md) `__declspec` modyfikator. Korzystanie z `noreturn` stanowi ponowna definicja funkcji; deklaracji i definicji należy uzgodnić użycie `noreturn`.  
  
 Poniższy przykład generuje C2381:  
  
```  
// C2381.cpp  
// compile with: /c  
void f1();  
void __declspec(noreturn) f1() {}   // C2381  
void __declspec(noreturn) f2() {}   // OK  
```