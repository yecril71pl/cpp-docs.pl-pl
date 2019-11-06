---
title: Ostrzeżenie kompilatora (poziom 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 71b23ec719198d15a99b4fcfd50db8b151e03226
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627353"
---
# <a name="compiler-warning-level-1-c4005"></a>Ostrzeżenie kompilatora (poziom 1) C4005

"Identyfikator": Ponowna definicja makra

Identyfikator makra jest definiowany dwa razy. Kompilator używa drugiej definicji makra.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Definiowanie makra w wierszu polecenia i w kodzie z dyrektywą `#define`.

1. Makra importowane z plików dołączanych.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Usuń jedną z definicji.

1. Przed drugą definicją Użyj dyrektywy [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) .

Poniższy przykład generuje C4005:

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```