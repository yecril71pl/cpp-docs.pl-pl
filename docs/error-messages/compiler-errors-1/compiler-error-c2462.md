---
title: Błąd kompilatora C2462 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65df7f4fe7f3822f2723a1709751e3b9b0f23ade
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082859"
---
# <a name="compiler-error-c2462"></a>Błąd kompilatora C2462

'Identyfikator': nie można zdefiniować typu w "nowe wyrażenie"

Nie można zdefiniować typu w dziedzinie operand `new` operatora. Definicja typu należy umieścić w osobnych instrukcji.

Poniższy przykład spowoduje wygenerowanie C2462:

```
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```