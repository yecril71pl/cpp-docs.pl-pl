---
title: Kompilator ostrzeżenie (poziom 1) C4618
ms.date: 11/04/2016
f1_keywords:
- C4618
helpviewer_keywords:
- C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
ms.openlocfilehash: b8f24df7465525b24ecd3871447bd873889b1e23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406395"
---
# <a name="compiler-warning-level-1-c4618"></a>Kompilator ostrzeżenie (poziom 1) C4618

Parametry dyrektywy pragma zawierają dołączony ciąg pusty; dyrektywa pragma została zignorowana

Przekazano pusty ciąg jako argument do **#pragma**.

Dyrektywa pragma została przetworzona, bez argumentu.

Poniższy przykład spowoduje wygenerowanie C4618:

```
// C4618.cpp
// compile with: /W1 /LD
#pragma code_seg("")   // C4618
```