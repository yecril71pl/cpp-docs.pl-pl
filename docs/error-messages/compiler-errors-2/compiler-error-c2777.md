---
title: Błąd kompilatora C2777 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2777
dev_langs:
- C++
helpviewer_keywords:
- C2777
ms.assetid: 5fe158c0-2a65-488a-aca2-61d4a8b32d43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57dc92e267004cbb41fa9a6153ddc09f9aeb6fc5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077441"
---
# <a name="compiler-error-c2777"></a>Błąd kompilatora C2777

tylko jedna metoda "put" może być określona dla właściwości

A [właściwość](../../cpp/property-cpp.md) modyfikator declspec ma więcej niż jedną `put` właściwości.

Poniższy przykład spowoduje wygenerowanie C2777:

```
// C2777.cpp
struct A {
   __declspec(property(put=PutProp,put=PutPropToo))   // C2777
   // try the following line instead
   // __declspec(property(put=PutProp))
      int prop;
   int PutProp(void);
   int PutPropToo(void);
};
```