---
title: Kompilator ostrzeżenie (poziom 1) C4218 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1970dd1bd231716f59508a7cca9f82d3e13151ae
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074050"
---
# <a name="compiler-warning-level-1-c4218"></a>Kompilator ostrzeżenie (poziom 1) C4218

użyto niestandardowego rozszerzenia: należy określić co najmniej klasę magazynu lub typ

Rozszerzenia Microsoft do domyślnego (/Ze) bez określania typu lub magazynu klasy przy deklarowaniu zmiennej. Domyślny typ to `int`.

## <a name="example"></a>Przykład

```
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Deklaracje te są nieprawidłowe w obszarze zgodności ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).