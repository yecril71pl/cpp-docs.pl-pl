---
title: Błąd CXX0019 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 61646462eeba4918a4993b23f7f4b394083296ce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195893"
---
# <a name="expression-evaluator-error-cxx0019"></a>Błąd CXX0019 programu Expression Evaluator

nieprawidłowe rzutowanie typu

Ewaluatora wyrażenia języka C nie może wykonać rzutowania typu jako zapisaną.

Ten błąd jest identyczny z CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Określony typ jest nieznany.

1. Wystąpiło zbyt wiele poziomów typu wskaźnika. Na przykład typ rzutowania

    ```
    (char **)h_message
    ```

   nie można obliczyć przy użyciu ewaluatora wyrażeń języka C.
