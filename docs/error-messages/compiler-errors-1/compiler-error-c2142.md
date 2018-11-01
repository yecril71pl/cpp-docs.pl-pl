---
title: Błąd kompilatora C2142
ms.date: 11/04/2016
f1_keywords:
- C2142
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
ms.openlocfilehash: eda60204e07fd025a8c62b19de70e8204f9f80f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502014"
---
# <a name="compiler-error-c2142"></a>Błąd kompilatora C2142

deklaracje funkcji różnią się, parametry zmiennej określone tylko w jednej z nich

Jedna deklaracja funkcji zawiera zmiennej listy parametrów. Nie ma innej deklaracji. ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) tylko.

Poniższy przykład spowoduje wygenerowanie C2142:

```
// C2142.c
// compile with: /Za /c
void func();
void func( int, ... );   // C2142
void func2( int, ... );   // OK
```