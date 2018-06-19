---
title: Kompilator C4112 ostrzeżenie (poziomy 1 i 4) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43718511af0d85f0c9026fe70b4749c4e3d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299282"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Kompilator C4112 ostrzeżenie (poziomy 1 i 4)
\#wiersz wymaga całkowitą z przedziału od 1 i numer  
  
 [#Line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektywa określa parametr liczba całkowita jest poza dozwolonym zakresem.  
  
 Jeśli określony parametr jest mniejszy niż 1, licznik wierszy jest zmieniany na 1. Jeśli określony parametr jest większa niż *numer*, która jest limit zdefiniowany przez kompilator, licznik wierszy jest bez zmian. Jest to ostrzeżenia poziomu 1, w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) i ostrzeżenie poziom 4 z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Poniższy przykład generuje C4112:  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```