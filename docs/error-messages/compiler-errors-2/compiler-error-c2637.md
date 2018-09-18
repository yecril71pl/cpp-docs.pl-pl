---
title: Błąd kompilatora C2637 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2637
dev_langs:
- C++
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6242183e1510565ece7d75085657764b1ddc4081
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101481"
---
# <a name="compiler-error-c2637"></a>Błąd kompilatora C2637

'Identyfikator': nie można modyfikować wskaźników do składowych danych

Wskaźnik do składowej danych nie może mieć konwencji wywoływania. Aby rozwiązać problem, Usuń konwencji wywołania lub deklarowany jest wskaźnik do funkcji składowej.

Poniższy przykład spowoduje wygenerowanie C2637:

```
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```