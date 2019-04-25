---
title: Błąd kompilatora C2854
ms.date: 11/04/2016
f1_keywords:
- C2854
helpviewer_keywords:
- C2854
ms.assetid: 917fec9c-790a-4149-8dfc-00d17a09199c
ms.openlocfilehash: a1c30e1fa0f70e5e7bb4b1c97421ca06913fc6f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281719"
---
# <a name="compiler-error-c2854"></a>Błąd kompilatora C2854

Błąd składni w #pragma hdrstop

`#pragma hdrstop` Zawiera nieprawidłową nazwę pliku. Opcjonalnie nazwy pliku w nawiasy i cudzysłowy może następować pragmy:

Poniższy przykład spowoduje wygenerowanie C2854:

```
// C2854.cpp
// compile with: /c
#pragma hdrstop( "\\source\\pchfiles\\myheader.pch" ]   // C2854
// try the following line instead
// #pragma hdrstop( "\\source\\pchfiles\\myheader.pch" )
```