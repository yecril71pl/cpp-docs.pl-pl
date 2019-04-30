---
title: Kompilator ostrzeżenie (poziom 1) C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385475"
---
# <a name="compiler-warning-level-1-c4319"></a>Kompilator ostrzeżenie (poziom 1) C4319

> "~": zero rozszerzanie "*type1*"to"*type2*' o większym rozmiarze

Wynik **~** — operator (dopełnienia bitowego) jest niepodpisany i następnie rozszerzone zero, gdy jest konwertowany na typ większe.

## <a name="example"></a>Przykład

W poniższym przykładzie `~(a - 1)` jest oceniane jako 32-bitowych unsigned wyrażenie długie i następnie konwertowany na 64-bitowy, zerowego rozszerzenia. Może to prowadzić do operacji nieoczekiwane wyniki.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
