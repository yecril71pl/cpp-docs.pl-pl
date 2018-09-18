---
title: Błąd kompilatora C2094 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2094
dev_langs:
- C++
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e3591fef423bc24562a2f2edf18f7f2774cfcc4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073528"
---
# <a name="compiler-error-c2094"></a>Błąd kompilatora C2094

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