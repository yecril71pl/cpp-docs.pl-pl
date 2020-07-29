---
title: Ostrzeżenie kompilatora (poziom 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: e694f96d7f6271686d1b2a19e5a12e5e08e1cfbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219953"
---
# <a name="compiler-warning-level-4-c4207"></a>Ostrzeżenie kompilatora (poziom 4) C4207

użyto niestandardowego rozszerzenia: rozszerzony formularz inicjatora

Przy użyciu rozszerzeń Microsoft (/ze) można inicjować niesizeową tablicę **`char`** w nawiasach klamrowych.

## <a name="example"></a>Przykład

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

Takie inicjalizacje są nieprawidłowe pod kątem zgodności ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
