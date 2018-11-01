---
title: Błąd kompilatora C3414
ms.date: 11/04/2016
f1_keywords:
- C3414
helpviewer_keywords:
- C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
ms.openlocfilehash: 86ed40f31ae17724700e9d2c68950027d0eefb69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608994"
---
# <a name="compiler-error-c3414"></a>Błąd kompilatora C3414

'składowa': nie można zdefiniować importowanej funkcji składowej

Element członkowski został zdefiniowany w kodzie, który także jest zdefiniowane w przywoływanym zestawie.

Poniższy przykład spowoduje wygenerowanie C3414:

```
// C3414a2.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

następnie wyszukaj:

```
// C3414b2.cpp
// compile with: /clr
#using <C3414a2.dll>

void MyClass::Test() {    // C3414
}

System::Object::Object() {    // C3414
}
```
