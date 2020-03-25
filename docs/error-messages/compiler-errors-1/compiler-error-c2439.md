---
title: Błąd kompilatora C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205364"
---
# <a name="compiler-error-c2439"></a>Błąd kompilatora C2439

"Identyfikator": nie można zainicjować elementu członkowskiego

Nie można zainicjować klasy, struktury lub składowej Unii.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Podjęto próbę zainicjowania pośredniej klasy bazowej lub struktury.

1. Próba zainicjowania dziedziczonego elementu członkowskiego klasy lub struktury. Dziedziczony element członkowski musi być zainicjowany przez konstruktora klasy lub struktury.
