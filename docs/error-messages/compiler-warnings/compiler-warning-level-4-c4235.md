---
title: Ostrzeżenie kompilatora (poziom 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: df80bec2294929be463425d74d4bf00421b368e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198435"
---
# <a name="compiler-warning-level-4-c4235"></a>Ostrzeżenie kompilatora (poziom 4) C4235

użyto niestandardowego rozszerzenia: słowo kluczowe "Keyword" nie jest obsługiwane w tej architekturze

Kompilator nie obsługuje użytego słowa kluczowego.

To ostrzeżenie jest automatycznie podwyższana do błędu. Jeśli chcesz zmodyfikować to zachowanie, użyj [#pragma ostrzeżenie](../../preprocessor/warning.md). Na przykład, aby C4235 na ostrzeżenie poziomu 2, użyj następującego wiersza kodu

```cpp
#pragma warning(2:4235)
```

w pliku kodu źródłowego.
