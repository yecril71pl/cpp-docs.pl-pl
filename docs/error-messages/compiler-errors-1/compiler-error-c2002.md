---
title: Błąd kompilatora C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208250"
---
# <a name="compiler-error-c2002"></a>Błąd kompilatora C2002

Nieprawidłowa stała znaku dwubajtowego

Stała znaków wielobajtowych jest nieprawidłowa.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Stała znaku dwubajtowego zawiera więcej bajtów niż oczekiwano.

1. Nie dołączono standardowego nagłówka STDDEF. h.

1. Znaki dwubajtowe nie mogą być łączone z zwykłymi literałami ciągu.

1. Stała znaku dwubajtowego musi być poprzedzona znakiem "L":

    ```
    L'mbconst'
    ```

1. Dla firmy C++Microsoft argumenty tekstowe dyrektywy preprocesora muszą mieć format ASCII. Na przykład dyrektywa `#pragma message(L"string")`, jest nieprawidłowa.
