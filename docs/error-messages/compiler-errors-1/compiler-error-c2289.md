---
title: Błąd kompilatora C2289 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2289
dev_langs:
- C++
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5bf284ee7ada4f32772b5f65ed0b983e08e5988
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067614"
---
# <a name="compiler-error-c2289"></a>Błąd kompilatora C2289

tym samym kwalifikator typu użyty więcej niż raz

Typ deklaracji lub definicji używa kwalifikator typu (`const`, `volatile`, `signed`, lub `unsigned`) więcej niż raz, co powoduje wystąpienie błędu w obszarze zgodności ANSI (**/Za**).

Poniższy przykład spowoduje wygenerowanie C2286:

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```