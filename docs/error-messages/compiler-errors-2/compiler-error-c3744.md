---
title: Błąd kompilatora C3744 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d644a621fc6d8e460e1b97e5baec360de8662365
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063726"
---
# <a name="compiler-error-c3744"></a>Błąd kompilatora C3744

__unhook musi mieć co najmniej 3 argumenty dla zdarzeń zarządzanych

[__Unhook](../../cpp/unhook.md) funkcji, należy wykonać trzy parametry, gdy jest używana w programie, który jest kompilowany dla zarządzanych rozszerzeń języka C++.

`__hook` i `__unhook` nie są zgodne z/CLR programowania. Zamiast tego użyj operatorów += i-=.

C3744 jest dostępna, przy użyciu opcji kompilatora przestarzałe **: oldsyntax**.
