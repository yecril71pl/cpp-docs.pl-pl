---
title: Błąd kompilatora C3769 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3769
dev_langs:
- C++
helpviewer_keywords:
- C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da57a883bcf66535a531e98e23b5927d37cadccd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042233"
---
# <a name="compiler-error-c3769"></a>Błąd kompilatora C3769

"type": zagnieżdżona klasa nie może mieć taką samą nazwę jako natychmiastowo otaczającą klasę

Zagnieżdżona klasa nie może mieć taką samą nazwę jako natychmiastowo otaczającą klasę.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3769.

```
// C3769.cpp
// compile with: /c
class x {
   class x {};   // C3769
   class y {
      class x{};   // OK
   };
};
```