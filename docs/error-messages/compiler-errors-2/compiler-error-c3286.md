---
title: "C3286 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3286
dev_langs: C++
helpviewer_keywords: C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80cda9575b604c9dd8e0000428c2d32a487079dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3286"></a>C3286 błąd kompilatora  
  
> "*specyfikator*": Zmienna iteracji nie może mieć żadnych specyfikatory klasy magazynowania  
  
Nie można określić klasy magazynu w zmiennej iteracji. Aby uzyskać więcej informacji, zobacz [klasy magazynu (C++)](../../cpp/storage-classes-cpp.md) i [dla poszczególnych usług, w](../../dotnet/for-each-in.md).  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład generuje C3286 i zawiera także odpowiednie użycie.  
  
```cpp  
// C3286.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p = { 1, 2, 3 };  
   for each (static int i in p) {}   // C3286   
   for each (int j in p) {}   // OK  
}  
```