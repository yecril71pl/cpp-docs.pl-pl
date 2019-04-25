---
title: Błąd kompilatora C2731
ms.date: 11/04/2016
f1_keywords:
- C2731
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
ms.openlocfilehash: 2bb00f972f4c12a00255a9820a768d01691f9940
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302897"
---
# <a name="compiler-error-c2731"></a>Błąd kompilatora C2731

'Identyfikator': funkcja nie może zostać przeciążony

Funkcje `main`, `WinMain`, `DllMain`, i `LibMain` nie mogą być przeciążone.

Poniższy przykład spowoduje wygenerowanie C2731:

```
// C2731.cpp
extern "C" void WinMain(int, char *, char *);
void WinMain(int, short, char *, char*);   // C2731
```