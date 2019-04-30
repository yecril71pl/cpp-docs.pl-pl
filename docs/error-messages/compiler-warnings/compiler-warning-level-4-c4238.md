---
title: Kompilator ostrzeżenie (poziom 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401036"
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