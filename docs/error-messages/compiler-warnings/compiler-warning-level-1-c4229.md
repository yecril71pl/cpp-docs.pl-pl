---
title: Ostrzeżenie kompilatora (poziom 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: 79e97949f1c2c999c2800a708461ca9c68de0a5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223229"
---
# <a name="compiler-warning-level-1-c4229"></a>Ostrzeżenie kompilatora (poziom 1) C4229

anachronizm: Modyfikatory dla danych są ignorowane

Używanie modyfikatora Microsoft, takiego jak **`__cdecl`** na deklaracji danych, jest nieaktualnym postępowaniem.

## <a name="example"></a>Przykład

```cpp
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```
