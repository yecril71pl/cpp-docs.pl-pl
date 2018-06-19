---
title: C2748 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2748
dev_langs:
- C++
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 336a2eb10f0a39f81547361e982aa744be88149e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236134"
---
# <a name="compiler-error-c2748"></a>C2748 błąd kompilatora
zarządzane lub utworzenia tablicy WinRT musi mieć rozmiaru tablicy lub inicjatora tablicy  
  
 A zarządzane lub tablicy WinRT został niewłaściwie sformatowany. Aby uzyskać więcej informacji, zobacz [tablicy](../../windows/arrays-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C2748 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```