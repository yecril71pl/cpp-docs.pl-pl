---
title: Kompilator ostrzeżenie (poziomy 2 i 3) C4008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd052b8dd6a0b70dd90ca076d0085675b33dc621
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091182"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilator ostrzeżenie (poziomy 2 i 3) C4008

'Identyfikator': atrybut "attribute" został zignorowany

Kompilator ignorowane `__fastcall`, **statyczne**, lub **wbudowane** atrybutu dla funkcji (ostrzeżenie poziom 3) lub dane (ostrzeżenie poziom 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. `__fastcall` atrybut z danymi.

1. **statyczne** lub **wbudowane** atrybutem **głównego** funkcji.