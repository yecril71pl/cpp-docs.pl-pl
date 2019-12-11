---
title: Ostrzeżenie kompilatora (poziom 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: 59803440966b8396ba231dc5a7265620c37f9cc1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991198"
---
# <a name="compiler-warning-level-4-c4343"></a>Ostrzeżenie kompilatora (poziom 4) C4343

\#dyrektywy pragma Optimize ("g", off) przesłania opcję/og

To ostrzeżenie jest prawidłowe tylko w kompilatorze Rodzina procesorów Itanium (IPF), zgłasza, że pragma [optymalizuje](../../preprocessor/optimize.md) overrode opcję kompilatora [/og](../../build/reference/og-global-optimizations.md) .

Poniższy przykład generuje C4343:

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```
