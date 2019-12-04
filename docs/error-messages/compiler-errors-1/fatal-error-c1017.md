---
title: Błąd krytyczny C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756945"
---
# <a name="fatal-error-c1017"></a>Błąd krytyczny C1017

nieprawidłowe wyrażenie stałej całkowitej

Wyrażenie w `#if` dyrektywie nie istnieje lub nie zostało oszacowane jako stała.

Stałe zdefiniowane przy użyciu `#define` muszą mieć wartości, które są obliczane do stałej całkowitej, jeśli są używane w dyrektywie `#if`, `#elif`lub `#else`.

Poniższy przykład generuje C1017:

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Możliwe rozwiązanie:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Ponieważ `CONSTANT_NAME` oblicza ciąg, a nie liczbę całkowitą, dyrektywa `#if` generuje błąd krytyczny C1017.

W innych przypadkach preprocesor oblicza niezdefiniowaną stałą jako zero. Może to spowodować niezamierzone wyniki, jak pokazano w poniższym przykładzie. `YES` jest niezdefiniowana, więc ma wartość zero. Wyrażenie `#if` `CONSTANT_NAME` zwraca wartość false, a kod, który ma być używany w `YES` jest usuwany przez preprocesor. `NO` jest również niezdefiniowana (zero), więc `#elif` `CONSTANT_NAME==NO` ma wartość true (`0 == 0`), powodując, że preprocesor pozostawia kod w `#elif` części instrukcji — dokładnie odwrotnie od zamierzonego zachowania.

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Aby zobaczyć dokładnie, jak kompilator obsługuje dyrektywy preprocesora, należy użyć [/p](../../build/reference/p-preprocess-to-a-file.md), [/e](../../build/reference/e-preprocess-to-stdout.md)lub [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).
