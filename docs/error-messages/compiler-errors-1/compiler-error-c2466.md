---
title: Błąd kompilatora C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230532"
---
# <a name="compiler-error-c2466"></a>Błąd kompilatora C2466

Nie można przydzielić tablicy stałego rozmiaru 0

Tablica jest przydzielony lub zadeklarowana o rozmiarze zero. Wyrażenie stałe, aby uzyskać rozmiar tablicy musi być liczbą całkowitą większą niż zero. Deklaracja tablicy przy użyciu zerowego indeks dolny jest dozwolony, tylko w przypadku klasy, struktury lub Unii i tylko z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

Poniższy przykład spowoduje wygenerowanie C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```