---
title: Błąd kompilatora C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 1555817de6e50ea27a021718c8b094efeaebacde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230847"
---
# <a name="compiler-error-c3551"></a>Błąd kompilatora C3551

"oczekiwany określony typ zwracany przez późny"

Jeśli używasz **`auto`** słowa kluczowego jako symbolu zastępczego dla zwracanego typu funkcji, musisz podać typ zwracany określony jako późny. W poniższym przykładzie typ zwracany funkcji z opóźnieniem `myFunction` jest wskaźnikiem do tablicy czterech elementów typu **`int`** .

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Zobacz także

[Automatycznie](../../cpp/auto-cpp.md)
