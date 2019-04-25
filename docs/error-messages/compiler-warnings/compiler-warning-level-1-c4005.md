---
title: Kompilator ostrzeżenie (poziom 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 76aab2160bd5f7918771dcf63b7297a869da751e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187342"
---
# <a name="compiler-warning-level-1-c4005"></a>Kompilator ostrzeżenie (poziom 1) C4005

'Identyfikator': ponowna definicja makra

Identyfikator — makro jest zdefiniowany jako dwa razy. Kompilator używa drugiego definicji makra.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Definiowanie makra w wierszu polecenia i w kodzie adresem `#define` dyrektywy.

1. Makra zaimportowane z plików dołączanych.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Usuń jedną z definicji.

1. Użyj [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) dyrektywy przed definicją drugiego.

Poniższy przykład spowoduje wygenerowanie C4005:

```
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