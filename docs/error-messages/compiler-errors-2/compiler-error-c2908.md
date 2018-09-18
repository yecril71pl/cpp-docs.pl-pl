---
title: Błąd kompilatora C2908 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2908
dev_langs:
- C++
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 913a01a21c75933688c55bbb79c3621124601745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053118"
---
# <a name="compiler-error-c2908"></a>Błąd kompilatora C2908

jawna specjalizacja; Utworzono już wystąpienie "template"

Specjalizacja szablonu podstawowego jest wcześniejsza niż jawnej specjalizacji.

Poniższy przykład spowoduje wygenerowanie C2908:

```
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```