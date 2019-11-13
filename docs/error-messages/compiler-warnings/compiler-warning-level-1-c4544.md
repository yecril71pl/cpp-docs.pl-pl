---
title: Ostrzeżenie kompilatora (poziom 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: 094662270569c7362b7bb3c4953a466b19ed2e65
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966485"
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