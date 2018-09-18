---
title: Błąd kompilatora C2400 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2400
dev_langs:
- C++
helpviewer_keywords:
- C2400
ms.assetid: 1ba441ee-73f9-42a5-bfe9-fbeab93808eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 303a0aacbcde0fcf495469ed9cb9310ddb7710e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115167"
---
# <a name="compiler-error-c2400"></a>Błąd kompilatora C2400

Błąd składni wbudowanego asemblera w "context"; znaleziono "token"

Token spowodował błąd składni w określonym kontekście.

Poniższy przykład spowoduje wygenerowanie — od C2400:

```
// C2400.cpp
// processor: x86
int main() {
   __asm {
      heh ax,bx;   // C2400, heh is not a valid x86 instruction
      mov ax,bx;   // OK
   }
}
```