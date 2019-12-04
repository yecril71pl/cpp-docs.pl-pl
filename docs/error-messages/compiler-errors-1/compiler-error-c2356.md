---
title: Błąd kompilatora C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759935"
---
# <a name="compiler-error-c2356"></a>Błąd kompilatora C2356

segment inicjalizacji nie może ulec zmianie podczas jednostki tłumaczenia

Możliwe przyczyny:

- `#pragma init_seg` poprzedzony kodem inicjalizacji segmentu

- `#pragma init_seg` poprzedzany przez inny `#pragma init_seg`

Aby rozwiązać ten problem, Przenieś kod inicjalizacji segmentu na początek modułu. Jeśli trzeba zainicjować wiele obszarów, przenieś je do oddzielnych modułów.

Poniższy przykład generuje C2356:

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
