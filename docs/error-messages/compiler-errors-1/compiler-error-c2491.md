---
title: "C2491 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2491
dev_langs: C++
helpviewer_keywords: C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 83b369d72b4d2ed296f6abeb68cc69b8c233326e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2491"></a>C2491 błąd kompilatora
"identyfikator": definicja dllimport funkcja nie jest dozwolona  
  
 Dane statyczne elementy członkowskie danych i funkcji mogą być deklarowane jako `dllimport`s, ale nie jest zdefiniowany jako `dllimport`s.  
  
 Aby rozwiązać ten problem, Usuń `__declspec(dllimport)` specyfikator w definicji funkcji.  
  
 Poniższy przykład generuje C2491:  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```