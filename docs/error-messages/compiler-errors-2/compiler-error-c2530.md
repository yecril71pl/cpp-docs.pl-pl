---
title: Błąd kompilatora C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737130"
---
# <a name="compiler-error-c2530"></a>Błąd kompilatora C2530

"Identyfikator": odwołania muszą być zainicjowane

Należy zainicjować odwołanie, jeśli zostało zadeklarowane, chyba że zostało już zadeklarowane:

- Za pomocą słowa kluczowego [extern](../../cpp/using-extern-to-specify-linkage.md).

- Jako element członkowski klasy, struktury lub Unii (i jest inicjowany w konstruktorze).

- Jako parametr w deklaracji lub definicji funkcji.

- Jako zwracany typ funkcji.

Poniższy przykład generuje C2530:

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
