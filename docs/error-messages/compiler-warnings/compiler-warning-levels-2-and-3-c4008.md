---
title: Kompilator ostrzeżenie (poziomy 2 i 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359972"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilator ostrzeżenie (poziomy 2 i 3) C4008

'Identyfikator': atrybut "attribute" został zignorowany

Kompilator ignorowane `__fastcall`, **statyczne**, lub **wbudowane** atrybutu dla funkcji (ostrzeżenie poziom 3) lub dane (ostrzeżenie poziom 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. `__fastcall` atrybut z danymi.

1. **statyczne** lub **wbudowane** atrybutem **głównego** funkcji.