---
title: Błąd kompilatora C2466 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d43ee9d09fba77db022177a06c6ebe95c65ff79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037843"
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