---
title: Błąd kompilatora C2723 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b1be2d81ecec7eb96fd9c1cd7e9938ce509f71e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072020"
---
# <a name="compiler-error-c2723"></a>Błąd kompilatora C2723

'Funkcja': "specyfikatora" niedozwolony specyfikator w definicji funkcji

Specyfikator nie może występować poza deklaracją klasy definicje funkcji. `virtual` Specyfikator może być określony tylko na deklarację funkcji członkowskiej w obrębie deklaracji klasy.

Poniższy przykład generuje C2723 i pokazuje, jak go naprawić:

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```