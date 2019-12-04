---
title: Błąd kompilatora C3239
ms.date: 11/04/2016
f1_keywords:
- C3239
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
ms.openlocfilehash: e3143714ff0080ff6890f4afb72521d212e31a4e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756401"
---
# <a name="compiler-error-c3239"></a>Błąd kompilatora C3239

"Type": wskaźnik do wskaźnika wnętrza/PIN jest niedozwolony przez środowisko uruchomieniowe języka wspólnego

Kompilator napotkał nieprawidłowy typ.

Poniższy przykład generuje C3229:

```cpp
// C3239.cpp
// compile with: /clr
int main() {
   interior_ptr<int>* pip0;   // C3239

   // OK
   int * pip1;
   interior_ptr<int> pip2;
   int ** pip;
}
```
