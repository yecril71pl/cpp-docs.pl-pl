---
title: Błąd kompilatora C3295 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8210aacf60c4c53faf50278e7494c90c58aa67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076427"
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