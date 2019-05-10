---
title: Błąd kompilatora C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: c55160c855a6188a616f957acee43e409b751b62
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447801"
---
# <a name="compiler-error-c3203"></a>Błąd kompilatora C3203

"type": szablon klasy Niewyspecjalizowana lub typ ogólny nie może służyć jako szablon lub argument rodzajowy dla szablonu lub parametru ogólnego "param", oczekiwano typu rzeczywistego

Nieprawidłowy argument jest przekazywany do szablonu klasy lub ogólny. Szablon klasy lub typ ogólny oczekuje, że typ jako parametr.

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual Studio 2005: nie można użyć szablonu klasy Niewyspecjalizowana jako argument szablonu na liście klas bazowych. Aby rozwiązać C3203, jawnie dodać parametry typu szablonu do nazwę klasy szablonu w przypadku używania go jako parametr szablonu na liście klas bazowych.

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