---
title: Błąd kompilatora C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 8db81afc348434e9ea2f57c991962fb15dc6bf98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220161"
---
# <a name="compiler-error-c3744"></a>Błąd kompilatora C3744

__unhook musi mieć co najmniej 3 argumenty dla zdarzeń zarządzanych

[`__unhook`](../../cpp/unhook.md)Funkcja musi przyjmować trzy parametry, gdy jest używany w programie kompilowanym dla Managed Extensions for C++.

**`__hook`** i **`__unhook`** nie są zgodne z **`/clr`** programowaniem. Zamiast tego użyj operatorów + = i-=.

C3744 jest osiągalna tylko przy użyciu przestarzałej opcji kompilatora **`/clr:oldSyntax`** .
