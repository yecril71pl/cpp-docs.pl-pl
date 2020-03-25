---
title: Ostrzeżenie kompilatora (poziom 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: 32bcd85b1cd1bb6c89678daae02f4f31a9318b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162975"
---
# <a name="compiler-warning-level-1-c4326"></a>Ostrzeżenie kompilatora (poziom 1) C4326

> typem zwracanym*funkcji "Function*" powinna być "*Type1*", a nie "*Type2*"

## <a name="remarks"></a>Uwagi

Funkcja zwróciła typ inny niż *Type1*. Na przykład przy użyciu [/za](../../build/reference/za-ze-disable-language-extensions.md), **Main** nie zwrócił **int**.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4326 i pokazuje, jak to naprawić:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
