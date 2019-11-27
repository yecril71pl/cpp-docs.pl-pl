---
title: Ostrzeżenie kompilatora (poziom 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541776"
---
# <a name="compiler-warning-level-4-c4234"></a>Ostrzeżenie kompilatora (poziom 4) C4234

użyto niestandardowego rozszerzenia: słowo kluczowe "Keyword" zarezerwowane do użytku w przyszłości

Kompilator nie implementuje jeszcze użytego słowa kluczowego.

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md). Na przykład, aby C4234 na problem z ostrzeżeniem poziomu 4,

```cpp
#pragma warning(2:4234)
```

w pliku kodu źródłowego.