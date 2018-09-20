---
title: Porównanie znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3412939bac9dace6f3abaacda75ed73d6e60f21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428073"
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