---
title: Błąd kompilatora C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 2c8164cad25d68ee61ff9fed7170482d5dfc9505
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386996"
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