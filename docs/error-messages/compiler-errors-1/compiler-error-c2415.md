---
title: Błąd kompilatora C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: a0cdd528eca8ea267c62e6d44752d29ae16830c4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205624"
---
# <a name="compiler-error-c2415"></a>Błąd kompilatora C2415

niewłaściwy typ operandu

Kod operacji nie używa operandów tego typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Kod operacji nie obsługuje liczby użytych operandów. Zapoznaj się z instrukcją Skorowidz języka zestawu, aby określić poprawną liczbę operandów.

1. Nowszy procesor obsługuje instrukcję z dodatkowymi typami. Dostosuj opcję [/arch (minimalna architektura procesora)](../../build/reference/arch-minimum-cpu-architecture.md) , aby użyć późniejszego procesora.
