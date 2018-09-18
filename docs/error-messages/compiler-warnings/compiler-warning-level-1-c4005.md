---
title: Kompilator ostrzeżenie (poziom 1) C4005 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4005
dev_langs:
- C++
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8be172086e316c991f461b3ac42f58739801cfa7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022971"
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