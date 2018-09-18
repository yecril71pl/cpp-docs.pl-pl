---
title: Błąd kompilatora C3199 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3199
dev_langs:
- C++
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ed917b3711f7f757b0a4ad89f0e6594ea1642a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027284"
---
# <a name="compiler-error-c3199"></a>Błąd kompilatora C3199

Nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie ścisłym

[Float_control](../../preprocessor/float-control.md) pragma zostało użyte do określenia model wyjątków zmiennopozycyjnych w obszarze [/FP](../../build/reference/fp-specify-floating-point-behavior.md) ustawienie inne niż **/FP: precise**.

Poniższy przykład spowoduje wygenerowanie C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```