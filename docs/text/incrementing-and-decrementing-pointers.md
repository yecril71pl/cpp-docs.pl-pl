---
title: "Inkrementacja i dekrementacja wskaźników | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 7c63b900b389edb2c62b69296f709619072f4511
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementacja i dekrementacja wskaźników
Użyj następujących wskazówek:  
  
-   Wskaż bajty wiodące, nie na końcu bajtów. Nie jest zwykle bezpieczne wskaźnika na bajt. Jest zwykle bezpieczniejsze Skanuj ciąg do przodu, a nie odwrotnie.  
  
-   Istnieją wskaźnika przyrostu/dekrementacja funkcje i makra dostępne przenieść całej znaków:  
  
    ```  
    sz1++;  
    ```  
  
     Staje się:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` i `_mbsdec` funkcje poprawnie zwiększyć i zmniejszyć w `character` jednostki, niezależnie od rozmiaru znaków.  
  
-   Zmniejsza należy wskaźnik do head ciągu, tak jak poniżej:  
  
    ```  
    sz2--;  
    ```  
  
     Staje się:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Alternatywnie head wskaźnik może być nieprawidłowy znak w ciągu tak, aby:  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Musi mieć wskaźnik do znanego bajtu prawidłowe.  
  
-   Należy zachować wskaźnik do poprzedni znak na szybsze wywołań `_mbsdec`.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Indeksy bajtowe](../text/byte-indices.md)