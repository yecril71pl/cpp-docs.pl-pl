---
title: Kompilator ostrzeżenie (poziom 1) C4964 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1644e4603bae36ec9d407294dea78a27e60539
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086671"
---
# <a name="compiler-warning-level-1-c4964"></a>Kompilator ostrzeżenie (poziom 1) C4964

Opcje optymalizacji nie zostały określone; informacje profilowe nie zostaną zebrane.

[/GL](../../build/reference/gl-whole-program-optimization.md) i [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) zostały określone, ale brak optymalizacji zażądano, dzięki czemu będą generowane żadne pliki .pgc, i w związku z tym, nie optymalizacji sterowanej profilem będzie możliwe.

Jeśli chcesz, aby pliki .pgc do wygenerowania po uruchomieniu aplikacji, należy określić jedną z [/O](../../build/reference/o-options-optimize-code.md) opcje kompilatora.

Poniższy przykład spowoduje wygenerowanie C4964:

```
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```