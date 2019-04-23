---
title: Błąd kompilatora C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777591"
---
# <a name="compiler-error-c3353"></a>Błąd kompilatora C3353

"delegowanie": delegat można tworzyć tylko z globalnej funkcji lub funkcji składowej typu zarządzanego lub typu WinRT

Delegatów, zadeklarowany za pomocą [delegować](../../extensions/delegate-cpp-component-extensions.md) — słowo kluczowe, mogą być deklarowane tylko w zakresie globalnym.

Poniższy przykład spowoduje wygenerowanie C3353:

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```