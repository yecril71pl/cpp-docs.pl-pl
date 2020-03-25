---
title: Ostrzeżenie kompilatora (poziom 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 551309757f5e76e230d0a275da94ac94ec30fb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163926"
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
