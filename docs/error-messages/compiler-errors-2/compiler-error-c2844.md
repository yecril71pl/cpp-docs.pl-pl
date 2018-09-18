---
title: Błąd kompilatora C2844 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd4cbdc30523563207fe2a66c1c5cb158f84c94
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092106"
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
