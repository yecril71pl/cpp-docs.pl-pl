---
title: Ostrzeżenie kompilatora (poziom 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: dc1efad7f18310727e2fdb756e49b95294357c4d
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965411"
---
# <a name="compiler-warning-level-1-c4470"></a>Ostrzeżenie kompilatora (poziom 1) C4470

dyrektywy kontroli zmiennoprzecinkowej zostały zignorowane w opcji/CLR

Dyrektywy pragma kontroli zmiennoprzecinkowej:

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

nie ma żadnego wpływu na [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Poniższy przykład generuje C4470:

```cpp
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```