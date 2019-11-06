---
title: Ostrzeżenie kompilatora (poziom 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 88ed48e9bf7057c55ee4004ca1bb1eb18cd4be51
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626164"
---
# <a name="compiler-warning-level-1-c4090"></a>Ostrzeżenie kompilatora (poziom 1) C4090

"Operation": różne kwalifikatory "modyfikator"

Zmienna użyta w operacji jest zdefiniowana z określonym modyfikatorem, który uniemożliwia jego modyfikację bez wykrywania przez kompilator. Wyrażenie jest kompilowane bez modyfikacji.

To ostrzeżenie może być spowodowane tym, że wskaźnik do elementu **const** lub `volatile` jest przypisany do wskaźnika, który nie został zadeklarowany jako wskazujący **stałą** lub `volatile`.

To ostrzeżenie jest wydawane dla programów C. W C++ programie kompilator zgłasza błąd: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Poniższy przykład generuje C4090:

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```