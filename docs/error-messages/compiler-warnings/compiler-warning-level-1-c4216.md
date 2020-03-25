---
title: Ostrzeżenie kompilatora (poziom 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 2521366a9f33e8c5b1b7d41951a7cb08adfc2561
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199826"
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
