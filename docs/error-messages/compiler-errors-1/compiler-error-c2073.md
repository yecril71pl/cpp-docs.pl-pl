---
title: Błąd kompilatora C2073 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2073
dev_langs:
- C++
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 950ca9551a605da392c1f033cb1784ff43a7fefc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112372"
---
# <a name="compiler-error-c2073"></a>Błąd kompilatora C2073

'Identyfikator': elementy częściowo zainicjowanej tablicy muszą mieć domyślnego konstruktora

Zbyt mało inicjatory zostały określone w tablicy, typy zdefiniowane przez użytkownika lub stałych. Jeśli jawna inicjatora i jego odpowiedniego konstruktora, nie są określone dla elementu członkowskiego tablicy, należy podać domyślnego konstruktora.

Poniższy przykład spowoduje wygenerowanie C2073:

```
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```