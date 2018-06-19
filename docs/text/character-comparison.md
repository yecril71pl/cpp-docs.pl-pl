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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b969783a19c0836a8ab81d75820fc688df3ef31e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854954"
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