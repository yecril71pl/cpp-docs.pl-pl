---
title: Ostrzeżenie kompilatora (poziom 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 3139d321bca64b9938badebdabccd3ca1eb96d11
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966264"
---
# <a name="compiler-warning-level-1-c4530"></a>Ostrzeżenie kompilatora (poziom 1) C4530

C++użyta procedura obsługi wyjątków, ale nie włączono semantyki operacji unwind. Określ/EHsc

C++Obsługa wyjątków została użyta, ale nie wybrano [/EHsc](../../build/reference/eh-exception-handling-model.md) .

Gdy opcja/EHsc nie została włączona, obiekt z automatycznym magazynem w ramce między funkcją, która wykonuje throw, a funkcją przechwytującą throw, nie zostanie zniszczony. Jednak obiekt z automatycznym magazynem utworzony w bloku **try** lub **catch** zostanie zniszczony.

Poniższy przykład generuje C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Skompiluj przykład za pomocą/EHsc, aby rozwiązać ten problem.