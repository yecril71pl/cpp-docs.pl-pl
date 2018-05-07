---
title: C3286 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc47c103e93fe1e4f20f5007c6688b5b6648bf32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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