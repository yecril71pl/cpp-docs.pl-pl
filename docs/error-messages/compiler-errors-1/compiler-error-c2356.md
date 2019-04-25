---
title: Błąd kompilatora C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302543"
---
# <a name="compiler-error-c2356"></a>Błąd kompilatora C2356

segment inicjalizacyjny nie może ulec zmianie podczas tłumaczenia jednostki

Możliwe przyczyny:

- `#pragma init_seg` poprzedzony przez kod inicjujący segmentu

- `#pragma init_seg` poprzedzony przez inny `#pragma init_seg`

Aby rozwiązać problem, należy przenieść kod inicjujący segment na początku tego modułu. Jeśli wiele obszarów, musi zostać zainicjowany, należy przenieść ich w oddzielnych modułów.

Poniższy przykład spowoduje wygenerowanie C2356:

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```