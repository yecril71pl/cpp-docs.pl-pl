---
title: Kompilatora (poziom 4) ostrzeżenie C4937 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed7b33889677a304d303873799f36430c38129a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4937"></a>Kompilator C4937 ostrzegawcze (poziom 4)
"Tekst1" i "Tekst2" są nierozróżnialne jako argumenty "dyrektywy"  
  
 Ze względu na sposób kompilator przetwarza argumenty dyrektywy, nazw, które mają znaczenie dla kompilatora, takich jak słowa kluczowe z wielu liczbami w postaci tekstu (podkreślenia jedno- i formularze), nie może być wyodrębnione.  
  
 Przykładami takich ciągów są __cdecl i \__forceinline.  Uwaga: w obszarze /Za, tylko formularze podwójne podkreślenia są włączone.  
  
 Poniższy przykład generuje C4937:  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```