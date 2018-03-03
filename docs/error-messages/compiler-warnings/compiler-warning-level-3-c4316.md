---
title: "Kompilatora (poziom 3) ostrzeżenie C4316 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8aaa769ddab0f0fc297a153a3d12cacd23e3c12e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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