---
title: Kompilatora (poziom 1) ostrzeżenie C4258 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08a182ed592119fd52247737988810f9ca66b45c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285918"
---
# <a name="compiler-warning-level-1-c4258"></a>Kompilator C4258 ostrzegawcze (poziom 1)
"Zmienna": definicja z pętli for jest zignorowana; Służy definicji z otaczającego zakresu"  
  
 W obszarze [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), zmienne zdefiniowane w [dla](../../cpp/for-statement-cpp.md) pętli się znaleźć poza zakresem po **dla** kończy się w pętli. To ostrzeżenie występuje, gdy zmienna o takiej samej nazwie jako zmiennej pętli, ale zdefiniowanych w pętli otaczającej, jest używana ponownie zawierający zakres **dla** pętli. Na przykład:  
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```