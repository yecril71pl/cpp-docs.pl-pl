---
title: Ostrzeżenie kompilatora (poziom 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 38b93c83f822bc5b856a46f0dd62ea275d2bf207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198721"
---
# <a name="compiler-warning-level-3-c4334"></a>Ostrzeżenie kompilatora (poziom 3) C4334

"operator": wynik 32-bit Shift niejawnie przekonwertowany na 64 bitów (czy został on 64-bitowe przesunięcia?)

Wynik 32-bitowego przesunięcia został niejawnie przekonwertowany na 64-bitowy, a kompilator podejrzewa, że przeznaczenie 64-bit zostało zamierzone.  Aby rozwiązać ten problem, należy użyć 64-bitowego przesunięcia lub jawnie rzutować wynik przesunięcia do 64-bitowego.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4334.

```cpp
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```
