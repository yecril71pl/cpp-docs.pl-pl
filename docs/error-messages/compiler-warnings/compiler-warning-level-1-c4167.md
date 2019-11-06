---
title: Ostrzeżenie kompilatora (poziom 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: aa81dc0cba264dd6ff37d3bdd521fce477b8b70d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624842"
---
# <a name="compiler-warning-level-1-c4167"></a>Ostrzeżenie kompilatora (poziom 1) C4167

Funkcja: dostępna tylko jako wewnętrzna funkcja

**Funkcja #pragma** próbuje wymusić użycie przez kompilator konwencjonalnego wywołania funkcji, która musi być używana w formie wewnętrznej. Pragma jest ignorowana.

Aby uniknąć tego ostrzeżenia, Usuń **funkcję #pragma**.

## <a name="example"></a>Przykład

```cpp
// C4167.cpp
// compile with: /W1
#include <malloc.h>
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only
int main(){}
```