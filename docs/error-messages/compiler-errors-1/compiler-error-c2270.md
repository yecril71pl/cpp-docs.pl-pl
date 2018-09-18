---
title: Błąd kompilatora C2270 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2270
dev_langs:
- C++
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb1c6d1028f5ea2a34693a5098a7a869f2ff80ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036933"
---
# <a name="compiler-error-c2270"></a>Błąd kompilatora C2270

'Funkcja': Modyfikatory niedozwolone dla funkcji niebędących funkcjami Członkowskimi

Funkcja niebędących jest zadeklarowana za pomocą [const](../../cpp/const-cpp.md), [volatile](../../cpp/volatile-cpp.md), lub innego modyfikatora model pamięci.

Poniższy przykład spowoduje wygenerowanie C2270:

```
// C2270.cpp
// compile with: /c
void func1(void) const;   // C2270, nonmember function

void func2(void);

class CMyClass {
public:
   void func2(void) const;
};
```