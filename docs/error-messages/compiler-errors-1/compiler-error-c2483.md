---
title: Błąd kompilatora C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 20b08c0d2cd89224ed3d3b8b34915deb947b0b4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205117"
---
# <a name="compiler-error-c2483"></a>Błąd kompilatora C2483

>"*Identyfikator*": obiekt z konstruktorem lub destruktorem nie może być zadeklarowany jako "Thread"

Ten komunikat o błędzie jest przestarzały w programie Visual Studio 2015 i nowszych wersjach. W poprzednich wersjach zmienne zadeklarowane z atrybutem `thread` nie mogą być inicjowane za pomocą konstruktora lub innego wyrażenia, które wymaga oceny czasu wykonywania. Do zainicjowania `thread` danych jest wymagane wyrażenie statyczne.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2483 w Visual Studio 2013 i wcześniejszych wersjach.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Zobacz też

[wątek](../../cpp/thread.md)
