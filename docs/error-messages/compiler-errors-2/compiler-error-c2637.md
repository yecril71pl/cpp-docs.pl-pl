---
title: Błąd kompilatora C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: 4231a811911fdf600b47962e929f6f3cff1f1bca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602541"
---
# <a name="compiler-error-c2637"></a>Błąd kompilatora C2637

'Identyfikator': nie można modyfikować wskaźników do składowych danych

Wskaźnik do składowej danych nie może mieć konwencji wywoływania. Aby rozwiązać problem, Usuń konwencji wywołania lub deklarowany jest wskaźnik do funkcji składowej.

Poniższy przykład spowoduje wygenerowanie C2637:

```
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```