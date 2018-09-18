---
title: Kompilator ostrzeżenie (poziom 1) C4006 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4006
dev_langs:
- C++
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35987244498b95dfee6f285f100237c3d3a361ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037052"
---
# <a name="compiler-warning-level-1-c4006"></a>Kompilator ostrzeżenie (poziom 1) C4006

\#undef Oczekiwano identyfikatora

`#undef` Dyrektywy nie określiła identyfikator, aby nie zdefiniowany. Dyrektywa jest ignorowany. Aby rozwiązać ostrzeżenia, należy określić identyfikator. Poniższy przykład spowoduje wygenerowanie C4006:

```
// C4006.cpp
// compile with: /W1
#undef   // C4006

// try..
// #undef TEST

int main() {
}
```