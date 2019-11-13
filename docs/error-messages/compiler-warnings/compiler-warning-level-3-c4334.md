---
title: Ostrzeżenie kompilatora (poziom 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: ebebfe9994be3dd136e3924cb2aea60c0c901926
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051635"
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