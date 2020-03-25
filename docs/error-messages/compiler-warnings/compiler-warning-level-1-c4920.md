---
title: Ostrzeżenie kompilatora (poziom 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: b587a4ca2a78bc2ac54640adb2b149d97bef4def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174664"
---
# <a name="compiler-warning-level-1-c4920"></a>Ostrzeżenie kompilatora (poziom 1) C4920

element członkowski wyliczenia wyliczenia składowa = wartość już widoczna w wyliczeniu wyliczenia jako element członkowski = wartość

Jeśli plik. tlb, który zostanie przekazany do #import ma ten sam symbol zdefiniowany w co najmniej dwóch wyliczeniach, to ostrzeżenie wskazuje, że kolejne identyczne symbole są ignorowane i zostaną oznaczone jako komentarz w pliku. tlh.

Przy założeniu, że TLB zawiera:

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

Poniższe przykłady generują C4920,

```cpp
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```
