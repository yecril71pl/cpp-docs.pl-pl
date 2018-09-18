---
title: Błąd kompilatora C3198 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb91d6f7b3ef6b8204a5f8bfb753db98ab6f93d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023387"
---
# <a name="compiler-error-c3198"></a>Błąd kompilatora C3198

Nieprawidłowe użycie zmiennoprzecinkowych pragm: fenv_access pragma działa tylko w trybie ścisłym

[fenv_access](../../preprocessor/fenv-access.md) pragma została użyta w obszarze [/FP](../../build/reference/fp-specify-floating-point-behavior.md) ustawienie inne niż **/FP: precise**.

Poniższy przykład spowoduje wygenerowanie C3198:

```
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```