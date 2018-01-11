---
title: "Ostatni znak w ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b766bec977f35f9f346723cbaf3f62e48c8c878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="last-character-in-a-string"></a>Ostatni znak w ciągu
Użyj następujących wskazówek:  
  
-   Dziennik zakresów bajtów nakładać się na zestaw w wielu przypadkach znaków ASCII. Można bezpiecznie bytewise skanowania dla żadnych znaków kontrolnych (mniej niż 32).  
  
-   Należy rozważyć użycie poniższego kodu, który może być sprawdzenie czy ostatni znak w ciągu jest znakiem ukośnika odwrotnego:  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     Ponieważ `strlen` nie jest MBCS-aware, zwraca liczbę bajtów nie liczbę znaków w ciągu wielobajtowe. Ponadto w przypadku Pamiętaj, że w niektórych kodu strony (932, na przykład), "\\" (0x5c) jest nieprawidłowy bajt (`sz` jest ciągiem C).  
  
     Możliwe rozwiązanie jest ponownie pisać kodu w ten sposób:  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     Ten kod używa funkcji MBCS `_mbsrchr` i `_mbsinc`. Ponieważ te funkcje są MBCS-aware, można odróżnić od "\\"znak i bajt"\\". Kod wykonuje akcję, jeśli ostatni znak w ciągu ma wartość null ('\0').  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Przypisanie znaku](../text/character-assignment.md)