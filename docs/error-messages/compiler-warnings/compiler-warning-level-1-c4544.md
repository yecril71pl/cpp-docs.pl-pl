---
title: Ostrzeżenie kompilatora (poziom 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: 6aee8ba6b07e02f012755f609d8a5089cea280b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186286"
---
# <a name="compiler-warning-level-1-c4544"></a>Ostrzeżenie kompilatora (poziom 1) C4544

"Deklaracja": domyślny argument szablonu został zignorowany dla tej deklaracji szablonu

Argument szablonu domyślnego został określony w niepoprawnej lokalizacji i został zignorowany. Domyślny argument szablonu dla szablonu klasy może być określony tylko w deklaracji lub definicji szablonu klasy, a nie w składowej szablonu klasy.

Ten przykład generuje C4545, a następny przykład pokazuje, jak rozwiązać ten problem:

```cpp
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

W tym przykładzie domyślny parametr ma zastosowanie do `S`szablonu klasy:

```cpp
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
