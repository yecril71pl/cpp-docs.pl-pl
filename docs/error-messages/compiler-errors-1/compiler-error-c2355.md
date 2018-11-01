---
title: Błąd kompilatora C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: 80871a73a7c3b4ad04b475539015f85d21ae88b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611285"
---
# <a name="compiler-error-c2355"></a>Błąd kompilatora C2355

"this": można tworzyć odwołania wyłącznie wewnątrz niestatycznych elementów członkowskich lub danych niestatycznych inicjatorów składowych

`this` Wskaźnik jest prawidłowy tylko wewnątrz niestatycznych elementów członkowskich lub w danych niestatycznych inicjatorów składowych. Ten błąd może spowodować, gdy zakres klasy definicji funkcji składowej, poza deklaracją klasy nie jest prawidłowo kwalifikowana. Ten błąd może również wystąpić, gdy `this` wskaźnik jest używany w funkcji, która nie jest zadeklarowana w klasie.

Aby rozwiązać ten problem, upewnij się, definicji funkcji składowej dopasowuje deklarację funkcji członkowskiej klasy i że jego nie jest zadeklarowany jako statyczny. Dla inicjatorów składowych danych upewnij się, że składowa danych nie jest zadeklarowany jako statyczny.

Poniższy przykład generuje C2355 i pokazuje, jak go naprawić:

```
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```