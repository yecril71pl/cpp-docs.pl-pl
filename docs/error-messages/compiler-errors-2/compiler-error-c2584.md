---
title: Błąd kompilatora C2584 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2584
dev_langs:
- C++
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0f8c523936473673f3af09400922e2594ed1891
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029432"
---
# <a name="compiler-error-c2584"></a>Błąd kompilatora C2584

"Class": bezpośrednie podstawowej "base2 —" jest niedostępny; już podstawowej "Base1 —"

`Class` już pochodzi bezpośrednio z `Base1`. `Base2` Ponadto pochodzi od klasy `Base1`. `Class` nie może pochodzić od `Base2` ponieważ oznacza to dziedziczenie (pośrednio) z `Base1` ponownie, który jest niedozwolone. ponieważ `Base1` jest już bezpośrednią klasą bazową.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2584.

```
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```