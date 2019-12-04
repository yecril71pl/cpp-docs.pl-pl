---
title: Błąd kompilatora C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: e44501f7df05a8b277cd52107ff35c4c4d30578f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759948"
---
# <a name="compiler-error-c2355"></a>Błąd kompilatora C2355

"This": można odwoływać się tylko wewnątrz niestatycznych funkcji składowych lub niestatycznych inicjatorów składowych danych

Wskaźnik `this` jest prawidłowy tylko wewnątrz niestatycznych funkcji składowych lub niestatycznych inicjatorów składowych danych. Ten błąd może wynikać z tego, że zakres klasy definicji funkcji składowej poza deklaracją klasy nie jest prawidłowo kwalifikowany. Ten błąd może również wystąpić, gdy `this` wskaźnik jest używany w funkcji, która nie jest zadeklarowana w klasie.

Aby rozwiązać ten problem, upewnij się, że definicja funkcji składowej pasuje do deklaracji funkcji składowej w klasie i że nie jest ona zadeklarowana jako statyczna. W przypadku inicjatorów składowych danych upewnij się, że element członkowski danych nie jest zadeklarowany jako statyczny.

Poniższy przykład generuje C2355 i pokazuje, jak to naprawić:

```cpp
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
