---
title: Kompilatora (poziom 1) ostrzeżenie C4114 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78402d4487eecde00c55ea5e0aad913d97226325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4114"></a>Kompilator C4114 ostrzegawcze (poziom 1)
Kwalifikator użyty więcej niż raz tego samego typu  
  
 Typ deklaracji lub definicji używa kwalifikator typu (**const**, `volatile`, **podpisany**, lub `unsigned`) więcej niż raz. Powoduje to ostrzeżenie z rozszerzeniami firmy Microsoft (/Ze) i błąd w obszarze Zgodność ANSI (/Za).  
  
 Poniższy przykład generuje C4114:  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 Poniższy przykład generuje C4114:  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```