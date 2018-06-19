---
title: Błąd narzędzi konsolidatora LNK1237 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ffc337d6b1548db4717dc4b87ff8aa25ef92e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298619"
---
# <a name="linker-tools-error-lnk1237"></a>Błąd narzędzi konsolidatora LNK1237
podczas generowania kodu kompilator wprowadził odwołanie do symbolu "symbol" zdefiniowanego w module "module" skompilowanym z opcją /GL  
  
 Podczas generowania kodu kompilator nie powinno wprowadzić symbole później rozwiązanych definicje skompilowany **/GL**. `symbol` to symbol, który został wprowadzony i później rozpoznać definicji skompilowane z **/GL**.  
  
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