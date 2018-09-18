---
title: Błąd kompilatora C2530 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f41f9ec64e2074ed5e0cd2654f2b6bfec886bc07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103198"
---
# <a name="compiler-error-c2530"></a>Błąd kompilatora C2530

'Identyfikator': odwołania muszą być zainicjowane

Należy zainicjować odwołanie jeśli zadeklarowano, o ile nie jest już zadeklarowana:

- Za pomocą słowa kluczowego [extern](../../cpp/using-extern-to-specify-linkage.md).

- Jako członek klasy, struktury lub Unii (i inicjalizacji w konstruktorze).

- Jako parametr w deklaracji lub definicji funkcji.

- Jako typ zwrotny funkcji.

Poniższy przykład spowoduje wygenerowanie C2530:

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```