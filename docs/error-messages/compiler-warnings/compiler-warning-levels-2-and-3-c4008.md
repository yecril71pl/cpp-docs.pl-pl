---
title: Ostrzeżenie kompilatora (poziomy 2 i 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198007"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Ostrzeżenie kompilatora (poziomy 2 i 3) C4008

"Identyfikator": atrybut "Attribute" został zignorowany

Kompilator zignorował atrybut `__fastcall`, **static**lub **inline** dla funkcji (ostrzeżenie poziomu 3) lub danych (poziom 2 ostrzeżenie).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. `__fastcall` atrybut z danymi.

1. atrybut **static** lub **inline** z funkcją **Main** .
