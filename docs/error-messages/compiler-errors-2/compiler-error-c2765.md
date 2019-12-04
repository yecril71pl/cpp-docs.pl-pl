---
title: Błąd kompilatora C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 0c646d0ab28b97b546721180e46b0f22ea376f7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759831"
---
# <a name="compiler-error-c2765"></a>Błąd kompilatora C2765

"Function": Jawna specjalizacja szablonu funkcji nie może mieć żadnych argumentów domyślnych

Argumenty domyślne są niedozwolone w jawnej specjalizacji szablonu funkcji. Aby uzyskać więcej informacji, zobacz [Jawna specjalizacja szablonów funkcji](../../cpp/explicit-specialization-of-function-templates.md).

Poniższy przykład generuje C2765:

```cpp
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```
