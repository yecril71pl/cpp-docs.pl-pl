---
title: Błąd kompilatora C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: 1d0ed5ec717efecb9fbea4a9451836c0471522b6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738716"
---
# <a name="compiler-error-c3203"></a>Błąd kompilatora C3203

"Type": Niewyspecjalizowany szablon klasy ani ogólny nie można użyć jako szablonu lub argumentu ogólnego dla szablonu lub parametru generycznego "param", oczekiwano typu rzeczywistego

Przeszedł nieprawidłowy argument do szablonu klasy lub generycznego. Szablon klasy lub generyczny oczekuje typu jako parametru.

Ten błąd może zostać wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio 2005: Niewyspecjalizowany szablon klasy nie może być używany jako argument szablonu na liście klas bazowych. Aby rozwiązać C3203, jawnie Dodaj parametry typu szablonu do nazwy klasy szablonu podczas używania jej jako parametru szablonu na liście klas bazowych.

```cpp
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

Poniższy przykład generuje C3203 i pokazuje, jak to naprawić:

```cpp
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

C3203 może również wystąpić przy użyciu typów ogólnych:

```cpp
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```
