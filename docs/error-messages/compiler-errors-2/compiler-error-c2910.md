---
title: Błąd kompilatora C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 58d56ad834b34425cda4ac7ba081eabd2424e451
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408358"
---
# <a name="compiler-error-c2910"></a>Błąd kompilatora C2910

'Funkcja': nie może być jawnie specjalizowany

Kompilator wykrył próbę jawnie specialize funkcji dwa razy.

Poniższy przykład spowoduje wygenerowanie C2910:

```
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

Jeśli spróbujesz jawne specjalizacja składowej szablonu nie mogą być też generowane C2910. Oznacza to można tylko jawne specjalizacja szablonu funkcji.

Poniższy przykład spowoduje wygenerowanie C2910:

```
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

Ten błąd będzie też można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana w Visual Studio .NET 2003:.

Dla kodu będą prawidłowe w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET, Visual c++, Usuń `template <>`.

Poniższy przykład spowoduje wygenerowanie C2910:

```
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```