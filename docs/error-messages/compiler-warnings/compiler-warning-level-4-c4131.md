---
title: Kompilator ostrzeżenie (poziom 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 24872bb0b42de77dde358dc29f99826b41638628
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516063"
---
# <a name="compiler-warning-level-4-c4131"></a>Kompilator ostrzeżenie (poziom 4) C4131

'Funkcja': używa deklaratora w starym stylu

Deklaracja określona funkcja nie jest w formie prototypu.

Deklaracje funkcji w starym stylu powinny być konwertowane do formularza prototypu.

Poniższy przykład przedstawia deklarację funkcji w starym stylu:

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

Poniższy przykład przedstawia formularz prototypu:

```
void addrec( char *name, int id )
{ }
```