---
title: Ostrzeżenie kompilatora (poziom 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: e925f315e8506453403b0a0eda75b7c2956cc05c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219940"
---
# <a name="compiler-warning-level-4-c4221"></a>Ostrzeżenie kompilatora (poziom 4) C4221

użyto niestandardowego rozszerzenia: "identifier": nie można zainicjować przy użyciu adresu automatycznej zmiennej

Przy użyciu domyślnych rozszerzeń Microsoft (/ze) można zainicjować typ agregacji (**Array**, **`struct`** lub **`union`** ) przy użyciu adresu lokalnej (automatycznej) zmiennej.

## <a name="example"></a>Przykład

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe pod kątem zgodności ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
