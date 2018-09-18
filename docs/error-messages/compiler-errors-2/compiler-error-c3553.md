---
title: Błąd kompilatora C3553 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3553
dev_langs:
- C++
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c91697b8fa4f04c040d92f8af3aa004bbde7a773
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118626"
---
# <a name="compiler-error-c3553"></a>Błąd kompilatora C3553

> decltype oczekuje wyrażenia nie typu

`decltype()` — Słowo kluczowe wymaga wyrażenia jako argument, a nie nazwę typu. Na przykład ostatnią instrukcję w następujący fragment kodu powoduje błąd C3553.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```