---
title: Błąd kompilatora C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: ccbbb7875fdae48fd00f87f9a63f3764c143daae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442838"
---
# <a name="compiler-error-c2756"></a>Błąd kompilatora C2756

'typ szablonu': domyślne szablonowe argumenty niedozwolone w składowej specjalizacji

Szablon częściowa specjalizacja nie może zawierać argument domyślny.

Poniższy przykład generuje C2756 i pokazuje, jak go naprawić:

```
// C2756.cpp
template <class T>
struct S {};

template <class T=int>
// try the following line instead
// template <class T>
struct S<T*> {};   // C2756
```