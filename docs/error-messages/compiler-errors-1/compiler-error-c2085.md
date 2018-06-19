---
title: C2085 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0fe489dbdd0934926a056bbc7e5539f40ca1ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169845"
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