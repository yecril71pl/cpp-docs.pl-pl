---
title: Błąd kompilatora C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: e63c3870a60194b72f1be8e1b401bbdef8fa47be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736727"
---
# <a name="compiler-error-c3873"></a>Błąd kompilatora C3873

"char": ten znak nie jest dozwolony jako pierwszy znak identyfikatora

C++ Kompilator postępuje zgodnie ze standardem c++ 11 w przypadku znaków, które są dozwolone w identyfikatorze. W identyfikatorze są dozwolone tylko niektóre zakresy znaków i uniwersalne nazwy znaków. Dodatkowe ograniczenia dotyczą początkowego znaku identyfikatora. Aby uzyskać więcej informacji i listę dozwolonych znaków i zakresów uniwersalnej nazwy znaków, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).

Zakres znaków dozwolony w identyfikatorze jest mniej restrykcyjny podczas kompilowania C++kodu/CLI. Identyfikatory w kodzie skompilowane przy użyciu/CLR powinny być zgodne ze [standardem ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Poniższy przykład generuje C3873:

```cpp
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```
