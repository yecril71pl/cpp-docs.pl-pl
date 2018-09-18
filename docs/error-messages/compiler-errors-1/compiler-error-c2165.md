---
title: Błąd kompilatora C2165 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2165
dev_langs:
- C++
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e9047b7f096c855bbefec745b454e2289c05e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101114"
---
# <a name="compiler-error-c2165"></a>Błąd kompilatora C2165

"— słowo kluczowe": nie można modyfikować wskaźników do danych

`__stdcall`, `__cdecl`, Lub `__fastcall` — słowo kluczowe, które spróbują zmodyfikować wskaźnik do danych.

Poniższy przykład spowoduje wygenerowanie C2165:

```
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```