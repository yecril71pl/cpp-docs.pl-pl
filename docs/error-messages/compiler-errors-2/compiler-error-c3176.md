---
title: Błąd kompilatora C3176 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3176
dev_langs:
- C++
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa2ec269061531688620b89279a9670982c72578
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104196"
---
# <a name="compiler-error-c3176"></a>Błąd kompilatora C3176

"type": nie można zadeklarować lokalnego typu wartościowego

Klasa może zostać zadeklarowany jako typ wartości w zakresie globalnym.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3176.

```
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```