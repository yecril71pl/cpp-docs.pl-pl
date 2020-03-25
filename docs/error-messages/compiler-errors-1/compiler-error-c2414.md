---
title: Błąd kompilatora C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: fbe627a57e5defc499a4bc5d463e0bf33494acba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205663"
---
# <a name="compiler-error-c2414"></a>Błąd kompilatora C2414

niedozwolona liczba operandów

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Kod operacji nie obsługuje liczby użytych operandów. Zapoznaj się z instrukcją Skorowidz języka zestawu, aby określić poprawną liczbę operandów.

1. Nowszy procesor obsługuje instrukcję z inną liczbą operandów. Dostosuj opcję [/arch (minimalna architektura procesora)](../../build/reference/arch-minimum-cpu-architecture.md) , aby użyć późniejszego procesora.
