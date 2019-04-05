---
title: Błąd kompilatora C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 7a627ce28e60f42dabcf0a257464a8bfbd58b9a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028630"
---
# <a name="compiler-error-c2483"></a>Błąd kompilatora C2483

>"*identyfikator*": obiekt o Konstruktor lub destruktor nie można zadeklarować jako "wątek"

Ten komunikat o błędzie jest przestarzała w programie Visual Studio 2015 i nowszych wersjach. W poprzednich wersjach, zmienne zadeklarowane za pomocą `thread` atrybutu nie można zainicjować za pomocą konstruktora lub inne wyrażenie, które wymaga czasu wykonywania oceny. Statyczne wyrażenie jest wymagane do zainicjowania `thread` danych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2483 w programie Visual Studio 2013 i wcześniejszych wersji.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Zobacz także

[wątek](../../cpp/thread.md)