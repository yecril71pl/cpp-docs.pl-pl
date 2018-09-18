---
title: Kompilator ostrzeżenie (poziom 4) C4238 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057031"
---
# <a name="compiler-warning-level-4-c4238"></a>Kompilator ostrzeżenie (poziom 4) C4238

użyto niestandardowego rozszerzenia: wartościowanie prawostronne klasy wykorzystane jako wartościowanie lewostronne

W celu zgodności z poprzednimi wersjami programu Visual C++, rozszerzenia Microsoft (**/Ze**) pozwalają na korzystanie z typu klasy jako rvalue w kontekście, który jawnie lub niejawnie przyjmuje adresu. W niektórych przypadkach, takich jak na poniższym przykładzie może to być niebezpieczne.

## <a name="example"></a>Przykład

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Użycie tych powoduje błąd w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).