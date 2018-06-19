---
title: Kompilatora (poziom 1) ostrzeżenie C4744 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a45207f85575c8047f673b415ce802dbac24318
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282831"
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