---
title: Błąd kompilatora C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: 9d9ba48b0607e7a30b8748d4e9ae4f7025f11dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165024"
---
# <a name="compiler-error-c2511"></a>Błąd kompilatora C2511

"identyfikator": przeciążona funkcja składowa nie znaleziono w "class"

Brak wersji funkcja jest zadeklarowana z określonymi parametrami.  Możliwe przyczyny:

1. Nieprawidłowe parametry przekazane do funkcji.

1. Parametry są przekazywane w nieprawidłowej kolejności.

1. Niepoprawne pisownię nazwy parametrów.

Poniższy przykład spowoduje wygenerowanie C2511:

```
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```