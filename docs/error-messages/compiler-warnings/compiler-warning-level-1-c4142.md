---
title: Ostrzeżenie kompilatora (poziom 1) C4142
ms.date: 11/04/2016
f1_keywords:
- C4142
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
ms.openlocfilehash: 3c9ab9c22d41e7732c86d43f5c6b4f09c50bbda8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196854"
---
# <a name="compiler-warning-level-1-c4142"></a>Ostrzeżenie kompilatora (poziom 1) C4142

niegroźna ponowna definicja typu

Typ jest ponownie definiowany w sposób, który nie ma wpływu na wygenerowany kod.

Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny:

- Funkcja członkowska klasy pochodnej ma inny typ zwracany od odpowiedniej funkcji członkowskiej klasy podstawowej.

- Typ zdefiniowany za pomocą **`typedef`** polecenia jest ponownie definiowany przy użyciu innej składni.

Poniższy przykład generuje C4142:

```c
// C4142.c
// compile with: /W1
float X2;
X2 = 2.0 + 1.0;   // C4142

int main() {
   float X2;
   X2 = 2.0 + 1.0;   // OK
}
```
