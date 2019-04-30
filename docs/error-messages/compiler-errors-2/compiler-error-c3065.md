---
title: Błąd kompilatora C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: e12f6e318d51ecaccc7c29e1e01d1aedcaac937e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404217"
---
# <a name="compiler-error-c3065"></a>Błąd kompilatora C3065

Deklaracja właściwości w zakresie nieklasowym nie jest dozwolone.

[Właściwość](../../cpp/property-cpp.md) __declspec — modyfikator użyto poza klasą.  Właściwości mogą być deklarowane tylko wewnątrz klasy.

Poniższy przykład spowoduje wygenerowanie C3065:

```
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```