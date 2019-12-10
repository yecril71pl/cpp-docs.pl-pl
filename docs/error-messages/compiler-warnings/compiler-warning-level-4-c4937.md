---
title: Ostrzeżenie kompilatora (poziom 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: dd7a7f9ac3d0ce0798a88f753cb0ccb4addbd5bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988751"
---
# <a name="compiler-warning-level-4-c4937"></a>Ostrzeżenie kompilatora (poziom 4) C4937

"Tekst1" i "Tekst2" są nierozróżniane jako argumenty dyrektywy "

Ze względu na sposób, w jaki kompilator przetwarza argumenty do dyrektyw, nazwy, które mają znaczenie dla kompilatora, takie jak słowa kluczowe z wieloma reprezentacjami tekstowymi (Formularze z pojedynczym i podwójnym podkreśleniem), nie można wyróżnić.

Przykładami takich ciągów są __cdecl i \__forceinline.  Uwaga w obszarze/za są włączone tylko formularze podwójnego podkreślenia.

Poniższy przykład generuje C4937:

```cpp
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
