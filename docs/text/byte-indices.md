---
title: Indeksy bajtowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: ec28ce5e577fe4d1e766934095d22a7e64a6a3da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="byte-indices"></a>Indeksy bajtowe
Użyj następujących wskazówek:  
  
-   Praca z bytewise indeksu na ciąg stanowi problem podobne do tych powodowanego przez manipulowania wskaźnika. Należy wziąć pod uwagę przykładzie skanował ciąg znaku ukośnika odwrotnego:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     To może indeksować bajt, nie bajtu, i dlatego nie może wskazywać na `character`.  
  
-   Użyj [_mbclen —](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) funkcji, aby rozwiązać problem poprzedniego:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     To poprawnie indeksuje do bajtu, dlatego aby `character`. `_mbclen` Funkcja określa rozmiar znaku (w bajtach 1 lub 2).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Ostatni znak w ciągu](../text/last-character-in-a-string.md)