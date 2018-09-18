---
title: Błąd krytyczny C1191 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1191
dev_langs:
- C++
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daefec7c89fc98d056963c4f761b7298d6e491cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062972"
---
# <a name="fatal-error-c1191"></a>Błąd krytyczny C1191

'dll' mogą być importowane w zakresie globalnym

Instrukcje Importuj biblioteki mscorlib.dll do programu, który używa programowania/CLR nie może występować w przestrzeni nazw lub funkcji, ale musi znajdować się w zakresie globalnym.

Poniższy przykład spowoduje wygenerowanie C1191:

```
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Możliwe rozwiązanie:

```
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```