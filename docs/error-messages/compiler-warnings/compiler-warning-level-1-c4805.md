---
title: Kompilator ostrzeżenie (poziom 1) C4805 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4805
dev_langs:
- C++
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fa9352dbd4138a755c603d332ff79232d7bb72a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103454"
---
# <a name="compiler-warning-level-1-c4805"></a>Kompilator ostrzeżenie (poziom 1) C4805

'Operacja': niebezpieczne połączenie typu "type" i typu "type" w operacji

To ostrzeżenie jest generowane dla operacji porównania między [bool](../../cpp/bool-cpp.md) i [int](../../c-language/integer-types.md). Poniższy przykład spowoduje wygenerowanie C4805:

```
// C4805.cpp
// compile with: /W1
int main() {
   int i = 1;
   bool b = true;

   if (i == b) {   // C4805, comparing bool and int variables
   }
}
```