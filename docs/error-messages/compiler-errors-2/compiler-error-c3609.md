---
title: Błąd kompilatora C3609 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3609
dev_langs:
- C++
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0048d1493a540bfb460d03ae514b6b191ead39d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016913"
---
# <a name="compiler-error-c3609"></a>Błąd kompilatora C3609

"członek": funkcja zapieczętowana ani końcowego musi być funkcją wirtualną

[Zapieczętowanego](../../windows/sealed-cpp-component-extensions.md) i [końcowego](../../cpp/final-specifier.md) słowa kluczowe są dozwolone tylko dla klasy, struktury lub element członkowski funkcji oznaczonej `virtual`.

Poniższy przykład spowoduje wygenerowanie C3609:

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
