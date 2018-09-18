---
title: Błąd kompilatora C3075 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3075
dev_langs:
- C++
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb2cbcb8908803cef2347fe5eb60342647094f95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023335"
---
# <a name="compiler-error-c3075"></a>Błąd kompilatora C3075

'instancja': nie można osadzić wystąpienia typu referencyjnego "type" w typie wartości

Typ wartości nie może zawierać wystąpienia typu referencyjnego.

Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów odwołań](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3075.

```
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```