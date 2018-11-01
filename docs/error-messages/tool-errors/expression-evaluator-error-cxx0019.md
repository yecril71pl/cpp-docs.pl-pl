---
title: Błąd CXX0019 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658097"
---
# <a name="expression-evaluator-error-cxx0019"></a>Błąd CXX0019 programu Expression Evaluator

Zły typ rzutowania

Ewaluator wyrażeń C nie można wykonać rzutowanie, jak zostały napisane typu.

Ten błąd jest taka sama jak CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Określony typ jest nieznany.

1. Wystąpiło zbyt wiele poziomów typów wskaźnika. Na przykład rzutowanie typu

    ```
    (char **)h_message
    ```

   Nie można obliczyć przez Ewaluator wyrażeń C.