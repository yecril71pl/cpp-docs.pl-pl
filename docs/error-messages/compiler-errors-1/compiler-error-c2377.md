---
title: Błąd kompilatora C2377
ms.date: 11/04/2016
f1_keywords:
- C2377
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
ms.openlocfilehash: b4789469fe27dafb2fb13bf3db085958db8d1478
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528768"
---
# <a name="compiler-error-c2377"></a>Błąd kompilatora C2377

'Identyfikator': zmiana definicji; Element TypeDef nie może zostać przeciążony przez dowolny inny symbol

A `typedef` identyfikator zostało przedefiniowane.

Poniższy przykład spowoduje wygenerowanie C2377:

```
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```