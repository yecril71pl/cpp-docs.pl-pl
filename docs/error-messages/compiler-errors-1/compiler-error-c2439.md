---
title: Błąd kompilatora C2439 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419bf7be45a1383135d0231cd059837e1fe62729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058416"
---
# <a name="compiler-error-c2439"></a>Błąd kompilatora C2439

'Identyfikator': nie można zainicjować składowej

Nie można zainicjować klasy, struktury lub Unii.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Podczas próby zainicjowania pośredniej klasy bazowej lub struktury.

1. Podczas próby zainicjowania dziedziczonej składowej klasy lub struktury. Dziedziczonej składowej musi zostać zainicjowany przez Konstruktor klasy lub struktury.