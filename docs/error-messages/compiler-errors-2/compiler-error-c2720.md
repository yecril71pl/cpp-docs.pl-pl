---
title: C2720 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6215cd2e83f1fa3a48c3cbd4970cd2d3466fc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2720"></a>C2720 błąd kompilatora  
  
> "*identyfikator*": "*specyfikator*" Specyfikator klasy składującej niedozwolony dla elementów członkowskich  
  
Klasa magazynu nie można używać w elementach członkowskich klasy poza deklaracji. Aby naprawić ten błąd, usuń zbędne [Klasa magazynu](../../cpp/storage-classes-cpp.md) specyfikator w definicji elementu członkowskiego spoza deklaracji klasy.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład generuje C2720 i pokazuje, jak rozwiązywanie problemu:  
  
```cpp  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
```