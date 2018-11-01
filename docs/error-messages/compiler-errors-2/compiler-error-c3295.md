---
title: Błąd kompilatora C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 63739989d737527e3f136bb3aac2269eda6231c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601698"
---
# <a name="compiler-error-c3295"></a>Błąd kompilatora C3295

"#pragma pragma" można używać tylko globalnie lub zakresie przestrzeni nazw

Niektóre informacje pragmatyczne nie można używać w funkcji.  Zobacz [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3295.

```
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```