---
title: Błąd kompilatora C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: 630e5b1cc6e99ffda28f50c09bccbbc2fea07172
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737702"
---
# <a name="compiler-error-c2612"></a>Błąd kompilatora C2612

znak "char" jest niedozwolony na liście inicjatora podstawowego/składowej

Znak pojawia się po ostatnim elemencie bazowym lub na liście inicjatorów.

Poniższy przykład generuje C2612:

```cpp
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```
