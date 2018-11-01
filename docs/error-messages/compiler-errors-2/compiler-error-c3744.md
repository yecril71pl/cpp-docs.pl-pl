---
title: Błąd kompilatora C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 407ed4b30b55b63aa9bf36de9f8675a531d70534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516236"
---
# <a name="compiler-error-c3744"></a>Błąd kompilatora C3744

__unhook musi mieć co najmniej 3 argumenty dla zdarzeń zarządzanych

[__Unhook](../../cpp/unhook.md) funkcji, należy wykonać trzy parametry, gdy jest używana w programie, który jest kompilowany dla zarządzanych rozszerzeń języka C++.

`__hook` i `__unhook` nie są zgodne z/CLR programowania. Zamiast tego użyj operatorów += i-=.

C3744 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
