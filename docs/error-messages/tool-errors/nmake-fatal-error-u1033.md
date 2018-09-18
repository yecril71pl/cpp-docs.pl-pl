---
title: Błąd krytyczny NMAKE U1033 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7492e5fd77f8e88b2191174f84c298c6166d8d89
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066385"
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