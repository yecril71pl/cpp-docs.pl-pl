---
title: Kompilator ostrzeżenie (poziom 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 314ee068fb2be6148304360b0aaa3bd8029c283b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401075"
---
# <a name="compiler-warning-level-4-c4234"></a>Kompilator ostrzeżenie (poziom 4) C4234

użyto niestandardowego rozszerzenia: słowo kluczowe "— słowo kluczowe" zarezerwowane dla przyszłego użytku

Kompilator nie implementuje jeszcze użyte słowo kluczowe.

To ostrzeżenie zostanie automatycznie podwyższony do błędu. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład, aby przekształcić C4234 ostrzeżenie poziom 4 problem

```
#pragma warning(2:4234)
```

w pliku kodu źródłowego.