---
title: Błąd kompilatora C2634 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2634
dev_langs:
- C++
helpviewer_keywords:
- C2634
ms.assetid: 58c8f2db-ac95-4a81-9355-ef3cfb0ba7b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 657e2ad5094fefe50a73957a85b59c4ffab9b2e3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026143"
---
# <a name="compiler-error-c2634"></a>Błąd kompilatora C2634

"& class::member": wskaźnik do odwołania składowej jest niedozwolony

Wskaźnik do odwołania składowej jest zadeklarowana.

Poniższy przykład spowoduje wygenerowanie C2634:

```
// C2634.cpp
int mem;
struct S {
   S() : rf(mem) { }
   int &rf;
};
int (S::*pdm) = &S::rf;   // C2634
```