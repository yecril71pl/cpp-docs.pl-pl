---
title: Kompilator ostrzeżenie (poziom 1) C4077 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4077
dev_langs:
- C++
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bf2b8f6f70db3d9cf385c87d1c9e71b4df05920
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044824"
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