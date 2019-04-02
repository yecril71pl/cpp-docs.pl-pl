---
title: Compiler Error C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 2676a32cee487595a2241359496ae9b0380126b8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775014"
---
# <a name="compiler-error-c2844"></a>Compiler Error C2844

'składowa': nie może być składową interfejsu "interface"

[Interfejsu klasy](../../extensions/interface-class-cpp-component-extensions.md) nie może zawierać element członkowski danych, chyba że jest to również właściwość.

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
