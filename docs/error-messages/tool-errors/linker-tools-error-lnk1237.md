---
title: "Błąd narzędzi konsolidatora LNK1237 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee9ec0e197d51f76ff57ef06f5584c55df0a4746
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1237"></a>Błąd narzędzi konsolidatora LNK1237
podczas generowania kodu kompilator wprowadził odwołanie do symbolu "symbol" zdefiniowanego w module "module" skompilowanym z opcją /GL  
  
 Podczas generowania kodu kompilator nie powinno wprowadzić symbole później rozwiązanych definicje skompilowany **/GL**. `symbol`to symbol, który został wprowadzony i później rozpoznać definicji skompilowane z **/GL**.  
  
 Aby uzyskać więcej informacji, zobacz [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 Rozwiązywać LNK1237 kompiluje symbol o **/GL** lub użyj [/include (Wymuszaj odwołania do symboli)](../../build/reference/include-force-symbol-references.md) wymuszenie odwołania do symbolu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK1237. Aby rozwiązać ten problem, nie inicjowanie tablicy w LNK1237_a.cpp i dodać **/ include: __chkstk** polecenia łącza.  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```