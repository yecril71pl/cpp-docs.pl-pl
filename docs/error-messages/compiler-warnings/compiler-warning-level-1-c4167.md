---
title: Ostrzeżenie kompilatora (poziom 1) C4167
ms.date: 11/04/2016
f1_keywords:
- C4167
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
ms.openlocfilehash: 99d60bc08a077ae1637b80eac6775c8fa2571a1e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163601"
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
