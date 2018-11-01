---
title: Porównywanie znaków
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 206910d4b76f93a92ee5230a227d6f0346a85e61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615413"
---
# <a name="character-comparison"></a>Porównywanie znaków

Użyj następujących wskazówek:

- Porównywanie znanych bajt znaku ASCII działa prawidłowo:

    ```cpp
    if( *sz1 == 'A' )
    ```

- Porównywanie dwóch znaków nieznany wymagane jest użycie jednego makra zdefiniowane w Mbstring.h:

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Daje to gwarancję, że oba bajty znaków dwubajtowych, są porównywane pod kątem równości.

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Przepełnienie buforu](../text/buffer-overflow.md)