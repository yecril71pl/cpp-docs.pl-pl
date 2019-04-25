---
title: Kompilator ostrzeżenie (poziom 1) C4006
ms.date: 11/04/2016
f1_keywords:
- C4006
helpviewer_keywords:
- C4006
ms.assetid: f1a59819-0fd2-4361-8e3a-99e4b514b8e1
ms.openlocfilehash: 97f50bdf4454a284953bd70e83574f5d0a86d1e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187290"
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