---
title: Ostrzeżenie kompilatora (poziom 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541760"
---
# <a name="compiler-warning-level-4-c4235"></a>Ostrzeżenie kompilatora (poziom 4) C4235

użyto niestandardowego rozszerzenia: słowo kluczowe "Keyword" nie jest obsługiwane w tej architekturze

Kompilator nie obsługuje użytego słowa kluczowego.

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md). Na przykład, aby C4235 na ostrzeżenie poziomu 2, użyj następującego wiersza kodu

```cpp
#pragma warning(2:4235)
```

w pliku kodu źródłowego.