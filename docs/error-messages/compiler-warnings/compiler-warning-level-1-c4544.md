---
title: Kompilator ostrzeżenie (poziom 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: f2a3f2e64a6a859add8182de4fc883c735563e92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352926"
---
# <a name="compiler-warning-level-1-c4544"></a>Kompilator ostrzeżenie (poziom 1) C4544

"deklaracją": Argument szablonu domyślnego został zignorowany dla tej deklaracji szablonu

Domyślny argument szablonu został określony w nieprawidłowej lokalizacji i został zignorowany. Domyślny argument szablonu dla szablonu klasy można określić tylko w deklaracji lub definicji szablonu klasy a nie w składowej szablonu klasy.

Ten przykład generuje C4545 i następny przykład pokazuje, jak go naprawić:

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

W tym przykładzie parametr domyślny ma zastosowanie do szablonu klasy `S`:

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```