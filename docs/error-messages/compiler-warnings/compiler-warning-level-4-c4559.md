---
title: Ostrzeżenie kompilatora (poziom 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 66e782c2fbb9c39c6a189de496cd0dcb4f1f4991
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218081"
---
# <a name="compiler-warning-level-4-c4559"></a>Ostrzeżenie kompilatora (poziom 4) C4559

> "*Function*": zmiana definicji; Funkcja zyskuje __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Funkcja została ponownie zdefiniowana lub ponownie zadeklarowana, a druga definicja lub Deklaracja dodała **`__declspec`** modyfikator (*modyfikator*). To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, Usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
