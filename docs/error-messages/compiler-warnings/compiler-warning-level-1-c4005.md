---
title: Ostrzeżenie kompilatora (poziom 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 4e95f8deeb61c5a4d56e0643beb6a746f848e33e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164732"
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
