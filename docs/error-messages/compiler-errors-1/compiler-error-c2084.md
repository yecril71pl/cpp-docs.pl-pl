---
title: Błąd kompilatora C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 0f7e049bc3f96e0a8e2b0a8cd306afeff52f7a5f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447329"
---
# <a name="compiler-error-c2084"></a>Błąd kompilatora C2084

Funkcja "*funkcja*" ma już treść

Funkcja została już zdefiniowana.

Before Visual Studio 2002,

- Kompilator będzie akceptować wielu specjalizacje szablonu, które rozwiązane do tego samego typu rzeczywistego, mimo że dodatkowe definicje nigdy nie będą dostępne. Kompilator wykrywa teraz te wiele definicji.

- `__int32` i `int` były traktowane jak oddzielne typy. Kompilator traktuje teraz `__int32` jako synonim dla `int`. Oznacza to, że kompilator wykrywa wiele definicji, jeśli funkcja jest przeciążona zarówno `__int32` i `int` i powoduje błąd.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

Aby rozwiązać ten problem, usuń zduplikowaną definicję:

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```