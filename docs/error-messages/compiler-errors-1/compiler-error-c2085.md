---
title: "C2085 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2085
dev_langs: C++
helpviewer_keywords: C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5834cbca32c2e3bb0c20ab39ee5d3b9d3e8e9c55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2085"></a>C2085 błąd kompilatora
'Identyfikator': nie znajduje się na liście parametrów formalnych  
  
 Identyfikator został zadeklarowany w definicji funkcji, ale nie na liście parametrów formalnych. (Tylko ANSI C)  
  
 Poniższy przykład generuje C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 Z brakującymi średnik `func1()` wygląda jak definicja funkcji, nie prototyp, więc `main` jest zdefiniowany w `func1()`, generowanie C2085 błąd dla identyfikatora `main`.