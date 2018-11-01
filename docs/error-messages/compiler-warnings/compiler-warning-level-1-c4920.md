---
title: Kompilator ostrzeżenie (poziom 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: cd501cf0e3b434523623276027056c93c77fc278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580694"
---
# <a name="compiler-warning-level-1-c4920"></a>Kompilator ostrzeżenie (poziom 1) C4920

Członek elementu członkowskiego wyliczenia typu wyliczeniowego = wartość już występuje w typie wyliczeniowym wyliczenia jako elementu członkowskiego = wartość

Jeśli .tlb, który jest przekazywany do #import ma ten sam symbolu, zdefiniowanego w co najmniej dwóch typów wyliczeniowych, to ostrzeżenie wskazuje, że kolejne identyczne symbole są ignorowane i będzie komentarzami w pliku .tlh.

Zakładając, że .tlb, który zawiera:

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

Poniższe przykłady generuje C4920,

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```