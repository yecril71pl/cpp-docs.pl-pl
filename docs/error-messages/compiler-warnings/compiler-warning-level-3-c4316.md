---
title: Kompilatora (poziom 3) ostrzeżenie C4316 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 609f3bbe9f338c5d53491190512ce2b9c290cdb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4316"></a>Kompilator C4316 ostrzegawcze (poziom 3)
Obiekt przydzielony na stosie nie może być wyrównane dla tego typu.  
  
 Obiekt wyrównany nadmiernie przydzielony przy użyciu `operator new` nie może mieć określone wyrównanie. Zastąpienie [nowy operator](../../c-runtime-library/operator-new-crt.md) i [operatora delete](../../c-runtime-library/operator-delete-crt.md) dla nadmiernie wyrównane typy tak, aby używały procedury alokacji wyrównany — na przykład [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) i [_aligned_free —](../../c-runtime-library/reference/aligned-free.md). Poniższy przykład generuje C4316:  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```