---
title: Błąd kompilatora C3637 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3637
dev_langs:
- C++
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 958ffc0d3aab641859b13570a94b159de80f2c7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117468"
---
# <a name="compiler-error-c3637"></a>Błąd kompilatora C3637

'Funkcja': definicja funkcji zaprzyjaźnionej nie może być specjalizacją typu funkcji

Funkcja zaprzyjaźniona niepoprawnie zdefiniowany dla szablon lub typ ogólny.

Poniższy przykład spowoduje wygenerowanie C3637:

```
// C3637.cpp
template <class T>
void f();

struct S {
   friend void f<int>() {}   // C3637
};
```

Możliwe rozwiązanie:

```
// C3637b.cpp
// compile with: /c
template <class T>
void f();

struct S {
   friend void f() {}
};
```

C3637 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3637c.cpp
// compile with: /clr

generic <class T>
void gf();

struct S {
   friend void gf<int>() {}   // C3637
};
```

Możliwe rozwiązanie:

```
// C3637d.cpp
// compile with: /clr /c
generic <class T>
void gf();

struct S {
   friend void gf() {}
};
```