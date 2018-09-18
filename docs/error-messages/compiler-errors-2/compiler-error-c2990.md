---
title: Błąd kompilatora C2990 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2990
dev_langs:
- C++
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0afceb82a58ee5c0a21e39fcaf4ba0a9ee9f2c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066976"
---
# <a name="compiler-error-c2990"></a>Błąd kompilatora C2990

"class": typ klasy korporacyjnej jako już został zadeklarowany jako typ klasy

Inne niż ogólne lub klasą szablonu redefiniuje generyczny lub szablonu klasy. Sprawdź pliki nagłówkowe dla konfliktów.

Poniższy przykład spowoduje wygenerowanie C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 może również wystąpić z powodu istotnej zmiany w kompilatorze języka Visual C++ dla Visual C++ 2005; Kompilator teraz wymaga wielu deklaracji dla tego samego typu identyczne w odniesieniu do specyfikacji szablonu.

Poniższy przykład spowoduje wygenerowanie C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```