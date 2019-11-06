---
title: Ostrzeżenie kompilatora (poziom 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 69559348a27151a22b11cae8d821110d923cd803
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627337"
---
# <a name="compiler-warning-level-1-c4216"></a>Ostrzeżenie kompilatora (poziom 1) C4216

użyto niestandardowego rozszerzenia: float Long

Domyślne rozszerzenia Microsoft (/ze) traktują wartości **zmiennoprzecinkowe** jako **Double**. Zgodność ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) nie jest zgodna z programem. Aby zachować zgodność, użyj **podwójnej precyzji** . Poniższy przykład generuje C4216:

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```