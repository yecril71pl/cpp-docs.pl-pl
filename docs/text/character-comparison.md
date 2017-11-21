---
title: "Porównanie znaków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0b9098dc20c33cccfd64631e7732be0128cb5bb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="character-comparison"></a>Porównywanie znaków
Użyj następujących wskazówek:  
  
-   Porównanie znanych bajtu ze znakiem ASCII działa prawidłowo:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Porównanie dwóch znaków nieznany wymaga użycia jednej z makra zdefiniowane w Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Dzięki temu, że oba bajty znaków dwubajtowych są porównywane pod kątem równości.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Przepełnienie buforu](../text/buffer-overflow.md)