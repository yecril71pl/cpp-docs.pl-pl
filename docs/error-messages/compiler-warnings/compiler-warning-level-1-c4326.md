---
title: Ostrzeżenie kompilatora (poziom 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: 41d8b271660ce0b6840e701ddac0f0538b265968
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87196555"
---
# <a name="compiler-warning-level-1-c4326"></a>Ostrzeżenie kompilatora (poziom 1) C4326

> typem zwracanym*funkcji "Function*" powinna być "*Type1*", a nie "*Type2*"

## <a name="remarks"></a>Uwagi

Funkcja zwróciła typ inny niż *Type1*. Na przykład przy użyciu [/za](../../build/reference/za-ze-disable-language-extensions.md), **Main** nie zwraca **`int`** .

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
