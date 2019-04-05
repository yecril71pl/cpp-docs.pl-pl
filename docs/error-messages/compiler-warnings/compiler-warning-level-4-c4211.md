---
title: Kompilator ostrzeżenie (poziom 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: cc80ddc459193c2e8fe5ca0b37d28d53d346fc53
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038112"
---
# <a name="compiler-warning-level-4-c4211"></a>Kompilator ostrzeżenie (poziom 4) C4211

użyto niestandardowego rozszerzenia: ponownie zdefiniowano extern jako static

Za pomocą domyślnego rozszerzenia Microsoft (/Ze), można ponownie zdefiniować `extern` identyfikator **statyczne**.

## <a name="example"></a>Przykład

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Takie definicji(-e) klas jest nieprawidłowa dla zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="see-also"></a>Zobacz także

