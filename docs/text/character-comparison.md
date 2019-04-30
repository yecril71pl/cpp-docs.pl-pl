---
title: Porównywanie znaków
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 075a22634f254c2ea634a1171ee157971fe5918e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410697"
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

## <a name="see-also"></a>Zobacz także

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Przepełnienie buforu](../text/buffer-overflow.md)
