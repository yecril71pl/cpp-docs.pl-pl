---
title: Błąd kompilatora C2703
description: Opis błędu kompilatora Microsoft C/C++ C2703.
ms.date: 08/24/2020
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 4d5b5ccad1cd15c1a107c81423e2372e14165776
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898611"
---
# <a name="compiler-error-c2703"></a>Błąd kompilatora C2703

> niedozwolona `__leave` instrukcja

## <a name="remarks"></a>Uwagi

**`__leave`** Instrukcja musi znajdować się wewnątrz **`__try`** bloku.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2703:

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```

## <a name="see-also"></a>Zobacz też

[`__leave`Słowo kluczowe](../../cpp/try-except-statement.md#__leave)\
[`try-except` Merge](../../cpp/try-except-statement.md)\
[`try-finally` Merge](../../cpp/try-finally-statement.md)
