---
title: Inkrementacja i dekrementacja wskaźników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fff5d7ec20ce052e4d831f1556432186ebc7bb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603363"
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementacja i dekrementacja wskaźników
Użyj następujących wskazówek:  
  
-   Wskaż bajty wiodące, nie końcu bajtów. Nie jest zwykle bezpieczne wskaźnika na bajt. Jest to zwykle bezpieczniejsze skanować ciąg do przodu, a nie w odwrotnej kolejności.  
  
-   Istnieją wskaźnika inkrementacyjnego/dekrementacyjnego funkcje i makra dostępne, które przenieść cały znaków:  
  
    ```  
    sz1++;  
    ```  
  
     staje się:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` i `_mbsdec` funkcje poprawnie zwiększyć i zmniejszyć w `character` jednostki, niezależnie od rozmiaru znaków.  
  
-   Dekrementuje należy wskaźnik porównanie ciągu, tak jak poniżej:  
  
    ```  
    sz2--;  
    ```  
  
     staje się:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Alternatywnie wskaźnik głównego może być nieprawidłowy znak w ciągu, tak, aby:  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Konieczne jest posiadanie wskaźnik do znanego, nieprawidłowy bajt.  
  
-   Możesz chcieć zachować wskaźnik do poprzedniego znaku na szybsze wywołań `_mbsdec`.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Indeksy bajtowe](../text/byte-indices.md)