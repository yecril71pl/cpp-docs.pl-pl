---
title: Błąd kompilatora C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: f9b3ea261db825f00004a2f447636c15d2d0d52e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759545"
---
# <a name="compiler-error-c2756"></a>Błąd kompilatora C2756

"typ szablonu": domyślne argumenty szablonu nie są dozwolone dla częściowej specjalizacji

Szablon częściowej specjalizacji nie może zawierać argumentu domyślnego.

Poniższy przykład generuje C2756 i pokazuje, jak to naprawić:

```cpp
// C2756.cpp
template <class T>
struct S {};

template <class T=int>
// try the following line instead
// template <class T>
struct S<T*> {};   // C2756
```
