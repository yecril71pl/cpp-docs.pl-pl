---
title: Błąd kompilatora C2787 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2787
dev_langs:
- C++
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4096e5dbd5b885afe3dec136a111ec69a10784f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109135"
---
# <a name="compiler-error-c2787"></a>Błąd kompilatora C2787

'Identyfikator': Brak GUID nie został skojarzony z tym obiektem

[__Uuidof](../../cpp/uuidof-operator.md) operator ma typ zdefiniowany przez użytkownika z identyfikatorem GUID dołączone lub obiektu takiego typu zdefiniowanego przez użytkownika. Ten błąd występuje, gdy argument jest typu zdefiniowanego przez użytkownika, za pomocą żaden identyfikator GUID.

Poniższy przykład spowoduje wygenerowanie C2787:

```
// C2787.cpp
#include <windows.h>
struct F {};

struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;

int main() {
   __uuidof(F);   // C2787
   __uuidof(F2);   // OK
}
```