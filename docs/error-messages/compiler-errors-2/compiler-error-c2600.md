---
title: Błąd kompilatora C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: 4d9e94790c3f4b2fa0aaf36894f0b12c7134a9ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62215669"
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