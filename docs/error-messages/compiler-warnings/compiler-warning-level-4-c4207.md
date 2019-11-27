---
title: Ostrzeżenie kompilatora (poziom 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: bd18964f8969bc75967de435e2ca3099b12213e0
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541877"
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