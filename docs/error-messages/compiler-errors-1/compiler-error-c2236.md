---
title: Błąd kompilatora C2236
ms.date: 11/04/2016
f1_keywords:
- C2236
helpviewer_keywords:
- C2236
ms.assetid: 0b6771a7-a783-4729-9c3d-7a3339c432cc
ms.openlocfilehash: 988377d2995468c84b86872ab6f2b25f5c3df9f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404315"
---
# <a name="compiler-error-c2236"></a>Błąd kompilatora C2236

Nieoczekiwany token 'Identyfikator'. Zapomnialeś ';'?

Identyfikator jest już zdefiniowany jako typ i nie może być zastąpiona przez typ zdefiniowany przez użytkownika.

Poniższy przykład spowoduje wygenerowanie C2236:

```
// C2236.cpp
// compile with: /c
int class A {};  // C2236 "int class" is unexpected
int i;
class B {};
```