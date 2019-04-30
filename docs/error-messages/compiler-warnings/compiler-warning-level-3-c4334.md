---
title: Kompilator ostrzeżenie (poziom 3) C4334
ms.date: 11/04/2016
f1_keywords:
- C4334
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
ms.openlocfilehash: 55512bf28c8c20512d0d245810d3e5c1fec36939
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402037"
---
# <a name="compiler-warning-level-3-c4334"></a>Kompilator ostrzeżenie (poziom 3) C4334

'operator': wynik 32-bitowe przesunięcia niejawnie skonwertowano do 64 bitów (była 64-bitowe przesunięcie przeznaczone?)

Wynik 32-bitowe przesunięcia niejawnie został przekonwertowany na 64-bitowej i kompilatora podejrzewa, że 64-bitowe przesunięcie było zamierzone.  Aby rozwiązać to ostrzeżenie, użyj 64-bitowe przesunięcie albo jawnie rzutowane wynik przesunięcia do 64-bitowej.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4334.

```
// C4334.cpp
// compile with: /W3 /c
void SetBit(unsigned __int64 *p, int i) {
   *p |= (1 << i);   // C4334
   *p |= (1i64 << i);   // OK
}
```