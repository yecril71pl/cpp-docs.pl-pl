---
title: Błąd kompilatora C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743825"
---
# <a name="compiler-error-c2466"></a>Błąd kompilatora C2466

nie można przydzielić tablicy o stałym rozmiarze 0

Tablica jest przypisana lub zadeklarowana z rozmiarem zero. Wyrażenie stałe dla rozmiaru tablicy musi być liczbą całkowitą większą od zera. Deklaracja tablicy z indeksem dolnym zero jest dozwolona tylko w przypadku klasy, struktury lub składowej Union i tylko z rozszerzeniami Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

Poniższy przykład generuje C2466:

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
