---
title: "C2720 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2720
dev_langs: C++
helpviewer_keywords: C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cfd1e41ea3b9479f07faa9a1cbf0739bc0b7e8b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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