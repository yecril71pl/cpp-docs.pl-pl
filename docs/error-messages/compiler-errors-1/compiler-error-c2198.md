---
title: "C2198 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2198
dev_langs: C++
helpviewer_keywords: C2198
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0da955515b5ad51836a82563fcfdf8d70de14470
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2198"></a>C2198 błąd kompilatora
"Funkcja": zbyt mało argumentów dla wywołania  
  
 Kompilator odnaleziono za mało parametrów dla wywołania funkcji lub deklaracji Niepoprawna funkcja.  
  
 Poniższy przykład generuje C2198:  
  
```  
// C2198.c  
// compile with: /c  
void func( int, int );  
int main() {  
   func( 1 );   // C2198 only one actual parameter  
   func( 1, 1 );   // OK  
}  
```