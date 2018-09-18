---
title: Błąd kompilatora C2355 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2355
dev_langs:
- C++
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 456049c60ce39fce3cdbf04512f306027e30db25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035191"
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