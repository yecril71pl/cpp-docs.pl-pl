---
title: "Kompilatora (poziom 1) ostrzeżenie C4744 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6fa95f8477f889aa8664d2b6d99c753cb9848d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4744"></a>Kompilator C4744 ostrzegawcze (poziom 1)
"var" ma inny typ w 'plik1' i 'plik2': "type1" i "type2".  
  
 Zewnętrzne zmienna zdefiniowana w dwóch plikach lub odwołuje się ma różne typy w tych plików.  Aby rozwiązać, ustalić definicji typu, taka sama lub zmienić nazwę zmiennej w jeden z plików.  
  
 C4744 jest emitowany tylko wtedy, gdy pliki są kompilowane przy użyciu/GL.  Aby uzyskać więcej informacji, zobacz [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).  
  
> [!NOTE]
>  C4744 zazwyczaj występuje w plikach C (C++ nie), ponieważ w języku C++ nazwę zmiennej ma informacje o typie.  Gdy próbki (poniżej) jest kompiluje jako C++, zostanie wyświetlony błąd konsolidatora LNK2019.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera pierwszy definicji.  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4744.  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```