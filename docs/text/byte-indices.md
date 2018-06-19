---
title: Indeksy bajtowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 509e66c7ea458519eaa9dc4f52c8a6b65c789d0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863803"
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