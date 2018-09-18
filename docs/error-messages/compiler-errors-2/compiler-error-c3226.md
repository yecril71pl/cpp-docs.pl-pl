---
title: Błąd kompilatora C3226 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3226
dev_langs:
- C++
helpviewer_keywords:
- C3226
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d0b070d5f32b75bdd3c56a3754857a574638b7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083252"
---
# <a name="compiler-error-c3226"></a>Błąd kompilatora C3226

Deklaracja szablonu nie jest dozwolona wewnątrz deklaracji ogólnej

Użyj deklaracji ogólnej wewnątrz klasy ogólnej.

Poniższy przykład spowoduje wygenerowanie C3226:

```
// C3226.cpp
// compile with: /clr
generic <class T>
ref class C {
   template <class T1>   // C3226
   ref struct S1 {};
};
```

W poniższym przykładzie pokazano możliwe rozwiązania:

```
// C3226b.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   generic <class T1>
   ref struct S1 {};
};
```