---
title: Ostrzeżenie kompilatora (poziom 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: fa9fc7d4a86ee686a9cd5d8d21412bd3346bcd80
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052564"
---
# <a name="compiler-warning-level-1-c4618"></a>Ostrzeżenie kompilatora (poziom 1) C4618

parametry dyrektywy pragma zawierają pusty ciąg; pragma ignorowana

Ciąg o wartości null został podany jako argument do **#pragma**.

Pragma została przetworzona bez argumentu.

Poniższy przykład generuje C4618:

```cpp
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```