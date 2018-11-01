---
title: Błąd kompilatora C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 8af9f42be279f728f72fc6968aeba98ee5d2474a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462715"
---
# <a name="compiler-error-c2844"></a>Błąd kompilatora C2844

'składowa': nie może być składową interfejsu "interface"

[Interfejsu klasy](../../windows/interface-class-cpp-component-extensions.md) nie może zawierać element członkowski danych, chyba że jest to również właściwość.

Coś innego niż właściwość lub funkcji składowej jest niedozwolony w interfejsie. Ponadto konstruktory, destruktory i operatory są niedozwolone.

Poniższy przykład spowoduje wygenerowanie C2844:

```
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
