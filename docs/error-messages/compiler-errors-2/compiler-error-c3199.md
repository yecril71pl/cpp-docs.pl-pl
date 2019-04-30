---
title: Compiler Error C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402791"
---
# <a name="compiler-error-c3199"></a>Compiler Error C3199

Nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie ścisłym

[Float_control](../../preprocessor/float-control.md) pragma zostało użyte do określenia model wyjątków zmiennopozycyjnych w obszarze [/FP](../../build/reference/fp-specify-floating-point-behavior.md) ustawienie inne niż **/FP: precise**.

Poniższy przykład spowoduje wygenerowanie C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```