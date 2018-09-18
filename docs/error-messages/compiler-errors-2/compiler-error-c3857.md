---
title: Błąd kompilatora C3857 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3857
dev_langs:
- C++
helpviewer_keywords:
- C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279ed343b57380df9db9180aa475e4d77ddf5ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097604"
---
# <a name="compiler-error-c3857"></a>Błąd kompilatora C3857

"type": wiele list parametrów typu nie są dozwolone.

Określono więcej niż jeden szablon lub ogólny tego samego typu, co jest niedozwolone.

Poniższy przykład spowoduje wygenerowanie C3857:

```
// C3857.cpp
template <class T, class TT>
template <class T2>    // C3857
struct B {};
```

Możliwe rozwiązanie:

```
// C3857b.cpp
// compile with: /c
template <class T, class TT, class T2>
struct B {};
```

C3857 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3857c.cpp
// compile with: /clr
generic <typename T>
generic <typename U>
ref class GC;   // C3857
```

Możliwe rozwiązanie:

```
// C3857d.cpp
// compile with: /clr /c
generic <typename U>
ref class GC;
```