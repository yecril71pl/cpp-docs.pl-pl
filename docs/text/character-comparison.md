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
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612329"
---
# <a name="character-comparison"></a>Porównywanie znaków
Użyj następujących wskazówek:  
  
-   Porównywanie znanych bajt znaku ASCII działa prawidłowo:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Porównywanie dwóch znaków nieznany wymagane jest użycie jednego makra zdefiniowane w Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Daje to gwarancję, że oba bajty znaków dwubajtowych, są porównywane pod kątem równości.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Przepełnienie buforu](../text/buffer-overflow.md)