---
title: Compiler Error C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 072c51ca4ae25c6f51b1841ea129a7b4fb495bdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377101"
---
# <a name="compiler-error-c2094"></a>Compiler Error C2094

Etykieta 'Identyfikator' nie została zdefiniowana

Etykietę używaną przez [goto](../../cpp/goto-statement-cpp.md) instrukcji nie istnieje w funkcji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2094:

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

Możliwe rozwiązanie:

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```