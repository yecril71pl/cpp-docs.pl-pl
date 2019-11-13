---
title: Ostrzeżenie kompilatora (poziom 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c293522e5d60d0edb4cc2da289e0ece71f89329f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052202"
---
# <a name="compiler-warning-level-2-c4094"></a>Ostrzeżenie kompilatora (poziom 2) C4094

nieoznakowany "token" zadeklarowany jako brak symboli

Kompilator wykrył pustą deklarację przy użyciu nieoznakowanej struktury, Unii lub klasy. Deklaracja jest ignorowana.

## <a name="example"></a>Przykład

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Ten stan generuje błąd w obszarze zgodność ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).