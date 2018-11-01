---
title: Błąd kompilatora C2890
ms.date: 11/04/2016
f1_keywords:
- C2890
helpviewer_keywords:
- C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
ms.openlocfilehash: 43c05fba15ee78c8e1454c115246f557f98f897e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661477"
---
# <a name="compiler-error-c2890"></a>Błąd kompilatora C2890

"class": klasa ref może mieć tylko jedną klasę bazową niebędącą interfejsem

Klasa odwołania może mieć tylko jedną klasę bazową.

Poniższy przykład spowoduje wygenerowanie C2890:

```
// C2890.cpp
// compile with: /clr /c
ref class A {};
ref class B {};
ref class C : public A, public B {};   // C2890
ref class D : public A {};   // OK
```
