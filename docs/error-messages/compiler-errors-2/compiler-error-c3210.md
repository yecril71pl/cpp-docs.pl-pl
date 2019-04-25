---
title: Błąd kompilatora C3210
ms.date: 11/04/2016
f1_keywords:
- C3210
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
ms.openlocfilehash: 9e0ac1aded7eef40be0e923b3ac1ebc9ef00c7a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182538"
---
# <a name="compiler-error-c3210"></a>Błąd kompilatora C3210

"type": deklaracja dostępu można stosować tylko do składowej klasy bazowej

A [użycie — deklaracja](../../cpp/using-declaration.md) została określona niepoprawnie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3210.

```
// C3210.cpp
// compile with: /c
struct A {
protected:
   int i;
};

struct B {
   using A::i;   // C3210
};

struct C : public A {
   using A::i;   // OK
};
```