---
title: Kompilator ostrzeżenie (poziom 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559849"
---
# <a name="compiler-warning-level-4-c4235"></a>Kompilator ostrzeżenie (poziom 4) C4235

użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" nie jest obsługiwane w tej architekturze

Kompilator nie obsługuje — słowo kluczowe, których użyto.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4235 do włączonego ostrzeżenia poziomu 2, należy użyć następującego kodu

```
#pragma warning(2:4235)
```

w pliku kodu źródłowego.