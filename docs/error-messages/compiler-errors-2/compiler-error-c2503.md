---
title: Błąd kompilatora C2503
ms.date: 11/04/2016
f1_keywords:
- C2503
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
ms.openlocfilehash: c481a27f19a92f47a19f0cfaa7b59cd509bb3c15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164946"
---
# <a name="compiler-error-c2503"></a>Błąd kompilatora C2503

"class": klasy bazowe nie mogą zawierać tablic o rozmiarze zerowym

Klasy bazowej lub struktury zawiera tablicę o rozmiarze zero. Tablica w klasie musi mieć co najmniej jeden element.

Poniższy przykład spowoduje wygenerowanie C2503:

```
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```