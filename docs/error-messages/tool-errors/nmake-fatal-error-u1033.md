---
title: Błąd krytyczny NMAKE U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 3b1df28e3cd7b27a9e7a130d9d71c1af68db9aec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445243"
---
# <a name="nmake-fatal-error-u1033"></a>Błąd krytyczny NMAKE U1033

Błąd składniowy: "string" Nieoczekiwany

Ciąg nie jest częścią prawidłowej składni dla pliku reguł programu make.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Jeśli zestaw zamykający nawias ostry (**<<**) dla pliku wbudowanego nie są wyświetlane na początku wiersza, wystąpi następujący błąd:

    ```
    syntax error : 'EOF' unexpected
    ```

1. Jeśli definicji makra w pliku reguł programu make zawiera znak równości (**=**) bez poprzedza nazwę lub jeśli nazwa definiowanego to makro, które rozszerza się na wartość nothing, wystąpi następujący błąd:

    ```
    syntax error : '=' unexpected
    ```

1. Jeśli średnik (**;**) w wierszu komentarza, w menu Narzędzia. INI nie jest na początku wiersza, wystąpi następujący błąd:

    ```
    syntax error : ';' unexpected
    ```

1. Jeśli w pliku reguł programu make został sformatowany przy użyciu edytora tekstu, może wystąpić następujący błąd:

    ```
    syntax error : ':' unexpected
    ```