---
title: Kompilator ostrzeżenie (poziom 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: 5171ee79c3afd32e847483568fbbf90222747509
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208353"
---
# <a name="compiler-warning-level-1-c4077"></a>Kompilator ostrzeżenie (poziom 1) C4077

Nieznana opcja check_stack

Stary formie **check_stack** pragmy jest używane z Nieznany argument. Argument musi być `+`, `-`, `(on)`, `(off)`, ani być pusta.

Kompilator ignoruje pragmy i pozostawia sprawdzania stosu bez zmian.

## <a name="example"></a>Przykład

```
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```