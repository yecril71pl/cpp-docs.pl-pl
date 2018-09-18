---
title: Kompilator ostrzeżenie (poziom 1) C4090 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ae34eeb6c87fdb12b07d25c6b6bbcfdd6b5ee21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024817"
---
# <a name="compiler-warning-level-1-c4090"></a>Kompilator ostrzeżenie (poziom 1) C4090

'Operacja': kwalifikatory innego modyfikatora

Zmienna użyty w operacji jest zdefiniowana za pomocą określonego modyfikatora, która zapobiega modyfikowaniu bez wykrycia przez kompilator. Wyrażenie jest kompilowany bez żadnych modyfikacji.

To ostrzeżenie może wystąpić, gdy wskaźnik do **const** lub `volatile` elementu jest przypisany do wskaźnika nie jest zadeklarowany jako wskazujący **const** lub `volatile`.

To ostrzeżenie zostanie wyświetlone dla programów C. W programie C++, kompilator generuje błąd: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

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