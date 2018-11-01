---
title: Błąd kompilatora C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: 32f39eb1d808ccedd27ae3e4d343b87ddfde1862
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666352"
---
# <a name="compiler-error-c3174"></a>Błąd kompilatora C3174

Moduł atrybut nie został określony.

Program, który używa atrybutów języka Visual C++ nie użyto również [modułu](../../windows/module-cpp.md) atrybut, który jest wymagany w przypadku dowolnego programu, który używa atrybutów.

Poniższy przykład spowoduje wygenerowanie C3174:

```
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```