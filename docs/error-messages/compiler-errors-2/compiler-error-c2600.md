---
title: Błąd kompilatora C2600 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1846cefa78c8df13e8ca3c1a7fbc142ba2bf6ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022087"
---
# <a name="compiler-error-c2600"></a>Błąd kompilatora C2600

'Funkcja': nie można zdefiniować generowanych przez kompilator specjalną funkcję członkowską (musi być zadeklarowana w klasie najpierw)

Przed elementu członkowskiego, które funkcje, takie jak konstruktory i destruktory mogą być definiowane dla klasy musi być zadeklarowana w klasie. Jeśli żaden nie został zadeklarowany w klasie, kompilator może wygenerować domyślne konstruktory i destruktory (nazywane funkcji specjalnych elementów członkowskich). Jednak jeśli zdefiniujesz jednej z tych funkcji bez pasującego deklaracji klasy, kompilator wykryje konflikt.

Aby naprawić ten błąd w deklaracji klasy, należy zadeklarować każda funkcja elementu członkowskiego, który definiuje poza deklaracją klasy.

Poniższy przykład spowoduje wygenerowanie od C2600 do:

```
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```