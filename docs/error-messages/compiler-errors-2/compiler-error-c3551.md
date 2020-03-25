---
title: Błąd kompilatora C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: e9a4ce2276a602d59e495a2f336bb9d59dc0cc99
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200762"
---
# <a name="compiler-error-c3551"></a>Błąd kompilatora C3551

"oczekiwany określony typ zwracany przez późny"

Jeśli używasz słowa kluczowego `auto` jako symbolu zastępczego dla zwracanego typu funkcji, musisz podać typ zwracany z opóźnieniem. W poniższym przykładzie, opóźniony określony typ zwracany funkcji `myFunction` jest wskaźnikiem do tablicy czterech elementów typu `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Zobacz też

[auto](../../cpp/auto-cpp.md)
