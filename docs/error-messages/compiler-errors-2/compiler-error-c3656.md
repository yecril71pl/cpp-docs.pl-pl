---
title: Błąd kompilatora C3656 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3656
dev_langs:
- C++
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c04e99d137d4235a0890cca56757f2e6fad70760
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072717"
---
# <a name="compiler-error-c3656"></a>Błąd kompilatora C3656

"override": Zastąp specyfikator nie może powtarzać się

Słowo kluczowe jawnego przesłaniania można określić tylko raz. Aby uzyskać więcej informacji, zobacz [jawne zastępowanie](../../windows/explicit-overrides-cpp-component-extensions.md).

Poniższy przykład spowoduje wygenerowanie C3656:

```
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```