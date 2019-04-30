---
title: Kompilator ostrzeżenie (poziom 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406486"
---
# <a name="compiler-warning-level-1-c4090"></a>Kompilator ostrzeżenie (poziom 1) C4090

'Operacja': kwalifikatory innego modyfikatora

Zmienna użyty w operacji jest zdefiniowana za pomocą określonego modyfikatora, która zapobiega modyfikowaniu bez wykrycia przez kompilator. Wyrażenie jest kompilowany bez żadnych modyfikacji.

To ostrzeżenie może wystąpić, gdy wskaźnik do **const** lub `volatile` elementu jest przypisany do wskaźnika nie jest zadeklarowany jako wskazujący **const** lub `volatile`.

To ostrzeżenie zostanie wyświetlone dla programów C. W C++ program, kompilator generuje błąd: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Poniższy przykład spowoduje wygenerowanie C4090:

```
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