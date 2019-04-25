---
title: Błąd kompilatora C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209039"
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