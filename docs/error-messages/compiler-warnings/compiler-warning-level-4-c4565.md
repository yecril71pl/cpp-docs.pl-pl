---
title: Ostrzeżenie kompilatora (poziom 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: ba2e1e7eb490a28626937a3911608ff9686d6f38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195983"
---
# <a name="compiler-warning-level-4-c4565"></a>Ostrzeżenie kompilatora (poziom 4) C4565

> "*Function*": zmiana definicji; Symbol został poprzednio zadeklarowany za pomocą __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Symbol został ponownie zdefiniowany lub ponownie zadeklarowany, a druga definicja lub Deklaracja, w przeciwieństwie do pierwszej definicji lub deklaracji, nie miała **`__declspec`** modyfikatora (*modyfikatora*). To ostrzeżenie jest informacje. Aby usunąć to ostrzeżenie, Usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
