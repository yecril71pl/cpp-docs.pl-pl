---
title: Ostrzeżenie kompilatora (poziom 1) C4077
ms.date: 11/04/2016
f1_keywords:
- C4077
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
ms.openlocfilehash: fb9684b812e039bd37278f9f27db9225d0131f23
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626900"
---
# <a name="compiler-warning-level-1-c4077"></a>Ostrzeżenie kompilatora (poziom 1) C4077

nieznana opcja check_stack

Stara forma dyrektywy pragma **check_stack** jest używana z nieznanym argumentem. Argument musi być `+`, `-`, `(on)`, `(off)`lub pusty.

Kompilator ignoruje pragmę i pozostawia sprawdzanie stosu bez zmian.

## <a name="example"></a>Przykład

```cpp
// C4077.cpp
// compile with: /W1 /LD
#pragma check_stack yes // C4077
#pragma check_stack +    // Correct old form
#pragma check_stack (on) // Correct new form
```