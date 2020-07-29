---
title: Ostrzeżenie kompilatora (poziomy 2 i 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: ab51b16331cc6a102c828234d2c2b8be84f2d276
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225244"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Ostrzeżenie kompilatora (poziomy 2 i 3) C4008

"Identyfikator": atrybut "Attribute" został zignorowany

Kompilator zignorował **`__fastcall`** **`static`** atrybut,, lub **`inline`** dla funkcji (ostrzeżenie poziomu 3) lub dane (poziom 2 ostrzeżenie).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. **`__fastcall`** atrybut z danymi.

1. **`static`** lub **`inline`** atrybut z funkcją **Main** .
