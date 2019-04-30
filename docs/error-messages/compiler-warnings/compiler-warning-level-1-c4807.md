---
title: Kompilator ostrzeżenie (poziom 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: a68596136e61aa33176365a4eff818124463b77e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390467"
---
# <a name="compiler-warning-level-1-c4807"></a>Kompilator ostrzeżenie (poziom 1) C4807

'Operacja': niebezpieczne połączenie typu "type" i podpisem bitfield typu "type"

To ostrzeżenie jest generowane, gdy porównanie pola bitowego ze znakiem jeden bit do `bool` zmiennej. Pole bitowe jeden bit, podpisem może zawierać tylko wartości -1 lub 0, dlatego jest niebezpieczne do porównywania go do `bool`. Żadne ostrzeżenia nie są generowane temat mieszania `bool` i pola bitów co bitowego, unsigned, ponieważ są one identyczne `bool` i może zawierać tylko 0 lub 1.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4807:

```
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```