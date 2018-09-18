---
title: Błąd ewaluatora wyrażeń CXX0019 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fba76b75c640917b3b99cd41500d682cb1b32f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031811"
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