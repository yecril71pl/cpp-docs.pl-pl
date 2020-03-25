---
title: Ostrzeżenie kompilatora (poziom 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173910"
---
# <a name="compiler-warning-level-4-c4234"></a>Ostrzeżenie kompilatora (poziom 4) C4234

użyto niestandardowego rozszerzenia: słowo kluczowe "Keyword" zarezerwowane do użytku w przyszłości

Kompilator nie implementuje jeszcze użytego słowa kluczowego.

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md). Na przykład, aby C4234 na problem z ostrzeżeniem poziomu 4,

```cpp
#pragma warning(2:4234)
```

w pliku kodu źródłowego.
