---
title: Błąd kompilatora C2002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87a7fe1513c695344676624ae1968060097c885
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116922"
---
# <a name="compiler-error-c2002"></a>Błąd kompilatora C2002

Nieprawidłowa stała dwubajtowego znaku

Stała znak wielobajtowy jest nieprawidłowa.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Stała dwubajtowego znaku zawiera większą liczbę bajtów, niż oczekiwano.

1. Standardowy nagłówek STDDEF.h nie jest włączony.

1. Znaki dwubajtowe, nie można połączyć z literały ciągów znaków zwykłych.

1. Stała dwubajtowego znaku musi być poprzedzona znakiem "L":

    ```
    L'mbconst'
    ```

1. Dla Microsoft C++ argumenty tekst dyrektywy preprocesora muszą być ASCII. Na przykład, dyrektywa `#pragma message(L"string")`, jest nieprawidłowy.