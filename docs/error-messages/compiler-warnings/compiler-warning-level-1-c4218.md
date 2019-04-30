---
title: Kompilator ostrzeżenie (poziom 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: 36d5de3b1270b41edfc391df960a556aca207709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386476"
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