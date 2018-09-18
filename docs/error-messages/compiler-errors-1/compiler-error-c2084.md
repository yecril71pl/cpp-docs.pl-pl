---
title: Błąd kompilatora C2084 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052117"
---
# <a name="compiler-error-c2084"></a>Błąd kompilatora C2084

Funkcja "*funkcja*" ma już treść

Funkcja została już zdefiniowana.

W wersjach programu Visual C++ przed Visual Studio 2002

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