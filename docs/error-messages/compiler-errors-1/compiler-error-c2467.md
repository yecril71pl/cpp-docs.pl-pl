---
title: "C2467 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2467
dev_langs: C++
helpviewer_keywords: C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a51321e6597bffe0dded58ffa481f054e770f9b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2467"></a>C2467 błąd kompilatora
Niedozwolona deklaracja "użytkownik zdefiniowany typu anonimowego"  
  
 Zdefiniowane przez użytkownika typu zagnieżdżonego została zadeklarowana. Jest to błąd podczas kompilowania kodu źródłowego C z opcją zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) włączone.  
  
 Poniższy przykład generuje C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```