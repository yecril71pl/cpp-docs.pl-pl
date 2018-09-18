---
title: Błąd kompilatora C3203 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3203
dev_langs:
- C++
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae0707bc56a812af77d30ac9dac8e945ee5e2aa6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082858"
---
# <a name="compiler-error-c3203"></a>Błąd kompilatora C3203

"type": szablon klasy Niewyspecjalizowana lub typ ogólny nie może służyć jako szablon lub argument rodzajowy dla szablonu lub parametru ogólnego "param", oczekiwano typu rzeczywistego

Nieprawidłowy argument jest przekazywany do szablonu klasy lub ogólny. Szablon klasy lub typ ogólny oczekuje, że typ jako parametr.

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: nie można użyć szablonu klasy Niewyspecjalizowana jako argument szablonu na liście klas bazowych. Aby rozwiązać C3203, jawnie dodać parametry typu szablonu do nazwę klasy szablonu w przypadku używania go jako parametr szablonu na liście klas bazowych.

```
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

Poniższy przykład generuje C3203 i pokazuje, jak go naprawić:

```
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

C3203 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```