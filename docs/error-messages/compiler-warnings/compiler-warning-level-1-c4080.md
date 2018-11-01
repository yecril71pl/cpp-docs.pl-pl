---
title: Kompilator ostrzeżenie (poziom 1) C4080
ms.date: 11/04/2016
f1_keywords:
- C4080
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
ms.openlocfilehash: a91963d524300c8768768a8a4615b1ab27e033e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599800"
---
# <a name="compiler-warning-level-1-c4080"></a>Kompilator ostrzeżenie (poziom 1) C4080

Oczekiwano identyfikatora dla nazwy segmentu; znaleziono "symbol"

Nazwa segmentu w [#pragma alloc_text](../../preprocessor/alloc-text.md) musi być ciąg lub identyfikator. Kompilator ignoruje pragmy, jeśli nie można odnaleźć prawidłowego identyfikatora.

Poniższy przykład spowoduje wygenerowanie C4080:

```
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```