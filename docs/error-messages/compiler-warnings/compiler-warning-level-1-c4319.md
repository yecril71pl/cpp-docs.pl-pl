---
title: Kompilatora (poziom 1) ostrzeżenie C4319 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1b5fe896ae7d8f43708b60ee4dda486ef08f428
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4319"></a>Kompilator C4319 ostrzegawcze (poziom 1)

> "~": zero rozszerzanie "*type1*"do"*type2*" większego rozmiaru

Wynik **~** — operator (dopełnienia bitowego) jest bez znaku, a następnie rozszerzony zero konwertowania na typ większy.

## <a name="example"></a>Przykład

W poniższym przykładzie `~(a - 1)` jest traktowane jako 32-bitowych wyrażenie długa bez znaku, a następnie konwertowana do 64-bitowy przez rozszerzenie zero. Może to prowadzić do operacji nieoczekiwane wyniki.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
