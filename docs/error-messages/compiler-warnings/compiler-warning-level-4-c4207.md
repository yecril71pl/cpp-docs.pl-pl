---
title: Ostrzeżenie kompilatora (poziom 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161389"
---
# <a name="compiler-warning-level-4-c4207"></a>Ostrzeżenie kompilatora (poziom 4) C4207

użyto niestandardowego rozszerzenia: rozszerzony formularz inicjatora

Za pomocą rozszerzeń Microsoft (/ze) można inicjować niesizeową tablicę `char` przy użyciu ciągu w nawiasach klamrowych.

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
