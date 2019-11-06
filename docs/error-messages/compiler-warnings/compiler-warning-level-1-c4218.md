---
title: Ostrzeżenie kompilatora (poziom 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f1db3eabc3b614019676dc4494e83104c62fe579
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627308"
---
# <a name="compiler-warning-level-1-c4218"></a>Ostrzeżenie kompilatora (poziom 1) C4218

użyto niestandardowego rozszerzenia: należy określić co najmniej klasę magazynu lub typ

Przy użyciu domyślnych rozszerzeń Microsoft (/ze) można zadeklarować zmienną bez określania typu lub klasy magazynu. Domyślny typ to `int`.

## <a name="example"></a>Przykład

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Takie deklaracje są nieprawidłowe pod kątem zgodności ze standardem ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).