---
title: Błąd kompilatora C2356 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfad1703b36e1cd995207d35b99b323c883f828
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065416"
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